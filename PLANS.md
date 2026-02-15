# SeaweedFS Enterprise Build & Packaging Plan

## Overview
Build, package, and secure SeaweedFS for STIG-compliant, FIPS-capable enterprise Linux deployment.

## Plan Components

### 1. Build Infrastructure
- Set up multi-architecture Go build system
- Implement FIPS and standard build modes
- Create version extraction from Git tags

### 2. Security Scanning Pipeline
- Integrate syft for SBOM generation (CycloneDX JSON, SPDX JSON)
- Add trivy and grype vulnerability scanning
- Configure pass/fail gates for CRITICAL/HIGH vulnerabilities

### 3. Package Creation
- DEB packages for Ubuntu 22.04 (amd64, arm64)
- RPM packages for Oracle Linux 8/9 (amd64, arm64)
- Use native tools: dpkg-buildpackage, rpmbuild

### 4. Filesystem & System Configuration
- Binary: /opt/weed/weed
- Config: /etc/default/weed/, /etc/weed/
- Logs: /var/log/weed/
- System user: weed:weed (no login, no home)

### 5. Systemd Service Templates
- weed-master@.service
- weed-volume@.service
- weed-filer@.service
- weed-s3@.service
- STIG-compliant hardening

### 6. Instance Management
- Config model in /etc/default/weed/weed.conf
- Override configs in /etc/weed/
- HAProxy integration for S3

### 7. Logging & Compliance
- Logrotate configuration
- SBOM generation
- GPG artifact signing

### 8. CI/CD Pipeline
- GitHub Actions or GitLab CI
- Matrix builds per architecture
- Complete artifact archive

### 9. Additional Enhancements
- SELinux policy module
- AppArmor profile
- Healthcheck script
- Pre-flight validation
