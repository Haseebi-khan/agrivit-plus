# Security Policy

## Supported Versions

Security fixes are currently provided for the latest version of the
`main` branch.

| Version | Supported |
|---------|-----------|
| main    | N/A       |
| Older releases | N/A |

## Reporting a Vulnerability

Please do not report security vulnerabilities through public GitHub issues.

Instead, report them privately to the project maintainers through the
security contact available in the repository's GitHub Security settings.

Please include:

- A clear description of the vulnerability.
- Steps required to reproduce the issue.
- The affected file, component, or workflow.
- Potential impact.
- Any suggested mitigation or fix.

## Sensitive Information

Do not include passwords, API keys, access tokens, private datasets,
credentials, or other sensitive information in issues or pull requests.

Never commit secrets such as:

```text
.env
API keys
cloud credentials
database passwords
access tokens
private dataset credentials

Use environment variables or GitHub Actions secrets where appropriate.

Responsible Disclosure

We ask security researchers and contributors to allow reasonable time
for the maintainers to investigate and address reported vulnerabilities
before publicly disclosing them.

Thank you for helping keep AgriViT-Plus and its contributors safe.


### Important

You should also have a `.gitignore` containing things such as:

```gitignore
.env
.env.*
!.env.example

__pycache__/
*.py[cod]

.venv/
venv/
*.egg-info/

weights/
checkpoints/

mylogs/
mlruns/

*.pt
*.pth
*.onnx

.DS_Store
.ipynb_checkpoints/
