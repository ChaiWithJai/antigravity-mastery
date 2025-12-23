# Deployment Workflow

Deploy the current project to staging or production.

## Input
Ask for:
- Environment: staging or production
- Confirmation for production deploys

## Pre-Deploy Checks

### 1. Code State
```bash
git status
git log -1 --oneline
```
Verify:
- [ ] No uncommitted changes
- [ ] On correct branch (main for production)

### 2. Tests
```bash
npm test
```
Verify:
- [ ] All tests pass
- [ ] No skipped tests (unless documented)

### 3. Build
```bash
npm run build
```
Verify:
- [ ] Build completes without errors
- [ ] No TypeScript errors
- [ ] No linting errors

## Staging Deploy

```bash
# Deploy to staging
npm run deploy:staging

# Wait for deployment
echo "Waiting for deployment to complete..."
sleep 30

# Smoke test
curl -I https://staging.example.com/health
```

Verify:
- [ ] Health check returns 200
- [ ] No new errors in logs

## Production Deploy

### Additional Checks (Production Only)
- [ ] Staging tested and verified
- [ ] Team notified in #deployments
- [ ] No active incidents

### Deploy Steps
```bash
# Announce
echo "Starting production deploy..."

# Deploy
npm run deploy:production

# Wait
sleep 30

# Verify
curl -I https://example.com/health
```

### Post-Deploy
- Monitor error rates for 15 minutes
- Check key metrics stable
- Respond to any alerts

## Rollback (If Needed)

```bash
# Rollback to previous version
npm run rollback

# Verify rollback
curl -I https://example.com/health
```

Immediately:
- Notify team in #deployments
- Create incident if user-facing impact
- Document what went wrong

## Output Format

```markdown
## Deployment Report

**Environment**: [staging/production]
**Time**: [timestamp]
**Version**: [commit hash]

### Pre-Deploy Checks
- [x] Tests passing
- [x] Build successful
- [x] On correct branch

### Deployment
- Status: [Success/Failed]
- Duration: [time]

### Verification
- Health check: [200 OK]
- Error rate: [normal/elevated]

### Notes
[Any issues or observations]
```
