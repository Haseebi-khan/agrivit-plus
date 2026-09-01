# Security Policy

## Supported Versions

AgriViT-Plus is currently under active development and does not have
official versioned releases yet.

Security updates are currently provided for the latest code available on
the `main` branch.

| Version                   | Supported          |
| ------------------------- | ------------------ |
| `main`                    | :white_check_mark: |
| Development branches      | :x:                |
| Unreleased/older versions | :x:                |

## Reporting a Vulnerability

Please **do not report security vulnerabilities through public GitHub
issues**.

If you discover a potential security vulnerability in AgriViT-Plus,
please report it privately through GitHub's **Security Advisories** feature
or contact the project maintainers privately.

### Please Include

When reporting a vulnerability, provide as much of the following information
as possible:

* A clear description of the vulnerability.
* The affected component, file, or functionality.
* Steps to reproduce the issue.
* Expected and actual behavior.
* Potential security impact.
* Relevant logs, screenshots, or error messages.
* A suggested fix or mitigation, if available.

Please avoid including sensitive information in the report.

## Sensitive Information

Never include the following information in public issues, pull requests,
or discussions:

* API keys
* Access tokens
* Passwords
* `.env` files
* Cloud credentials
* Database credentials
* Private dataset credentials
* Private or personally identifiable information

Use environment variables and GitHub repository secrets where appropriate.

## Responsible Disclosure

We ask security researchers and contributors to allow the maintainers
reasonable time to investigate and address reported vulnerabilities before
publicly disclosing them.

Please avoid publicly discussing an unresolved vulnerability until the
maintainers have had an opportunity to assess and address the issue.

## Response Process

After receiving a vulnerability report, the maintainers will:

1. Acknowledge receipt of the report.
2. Review and attempt to reproduce the reported issue.
3. Assess its severity and potential impact.
4. Develop and test an appropriate fix where necessary.
5. Release or deploy the fix when appropriate.
6. Notify the reporter when the issue has been addressed.

Response times may vary depending on the severity and complexity of the
reported vulnerability.

## Scope

This security policy applies to the AgriViT-Plus source code, training
pipeline, data-processing utilities, deployment/export scripts, and other
software components maintained in this repository.

Third-party dependencies and external datasets may have their own security
policies and should be reported to their respective maintainers when
appropriate.

## Security Best Practices for Contributors

Contributors should:

* Never commit credentials or secrets.
* Review changes for accidental exposure of sensitive information.
* Keep dependencies reasonably up to date.
* Avoid committing private datasets or personally identifiable information.
* Use `.gitignore` to prevent accidental inclusion of local credentials,
  logs, checkpoints, and other sensitive or large files.
* Follow the project's contribution guidelines when submitting changes.

Thank you for helping keep AgriViT-Plus secure.
