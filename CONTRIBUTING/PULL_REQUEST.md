<!-- TOC --><a name="-creating-a-pull-request"></a>
# 🔄 Creating a Pull Request
Follow these steps to contribute code to the core repository:

1. Fork the Repository
If you don’t have write access:
- Click Fork on the top-right of core.
- Clone your fork:
```bash
git clone https://github.com/your-username/core.git
cd core
```
If you have write access, clone the repo directly and work off the `main` branch.

2. Create a New Branch
Always branch from main:
```bash
git checkout -b feat/scheduler-prioritization
git checkout -b fix/etcd-client-config-errors
git checkout -b test/file-utils-unit-test-and-coverage
```
Use a descriptive name based on the feature or fix you're working on.

3. Make Your Changes
- Follow all 📜 Contribution Principles
- Write or update unit tests
- Validate your code:
```bash
make test    # Runs tests with coverage and race detection
make lint    # Runs static analysis via golangci-lint
```

3. Use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) to allow automatic changelog generation:
```
feat(scheduler): add weighted fair implementation
fix(storage): correct dequeue starvation logic
test: add fuzzing for wireframe decoding
```
```bash
git add .
git commit -m "feat(scheduler): add priority aging strategy"
```

4. Push and Open a PR
```bash
git push origin feat/scheduler-prioritization
```
Then:
- Go to your fork on GitHub
- Click "Compare & pull request"
- Fill out the PR template (description, motivation, test coverage, etc.)
- Link issues (e.g., `Fixes #42`) if applicable

5. Participate in Review
- Respond to comments and make updates as needed
- Use `git commit --amend` or `git rebase -i` for a clean commit history
- Push updates to the same branch to trigger CI reruns
Once your PR is merged:
- Sync your local main
- Delete the feature branch:
```bash
git checkout main
git pull origin main
git branch -d feat/scheduler-prioritization
```

> ### Next
> [Releases](./RELEASE.md)