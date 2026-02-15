# Tasks for SeaweedFS Enterprise Build & Packaging

## Phase 1: Build System
- [ ] 1.1 Create Makefile with multi-arch build targets (linux/amd64, linux/arm64)
- [ ] 1.2 Implement FIPS build flag support (FIPS_ENABLED=true)
- [ ] 1.3 Add version extraction from Git tags
- [ ] 1.4 Configure reproducible build flags
- [ ] 1.5 Add CGO and Go toolchain configuration

## Phase 2: Security Scanning
- [ ] 2.1 Add syft SBOM generation (CycloneDX JSON + SPDX JSON)
- [ ] 2.2 Add trivy vulnerability scanning
- [ ] 2.3 Add grype vulnerability scanning
- [ ] 2.4 Configure CRITICAL/HIGH vulnerability gates
- [ ] 2.5 Create artifact archiving for scan reports

## Phase 3: DEB Packaging (Ubuntu 22.04)
- [ ] 3.1 Create debian/control file
- [ ] 3.2 Create debian/rules file
- [ ] 3.3 Create debian/postinst script (user creation, permissions, systemd enable)
- [ ] 3.4 Create debian/postrm script (user removal on purge)
- [ ] 3.5 Create debian/preinst script
- [ ] 3.6 Build amd64 and arm64 packages

## Phase 4: RPM Packaging (Oracle Linux 8/9)
- [ ] 4.1 Create seaweedfs.spec file
- [ ] 4.2 Define %pre script (user creation)
- [ ] 4.3 Define %post script (permissions, systemd enable)
- [ ] 4.4 Define %preun/%postun scripts (user removal on purge)
- [ ] 4.5 Build for Oracle Linux 8 amd64/arm64
- [ ] 4.6 Build for Oracle Linux 9 amd64/arm64

## Phase 5: Systemd Templates
- [ ] 5.1 Create weed-master@.service template
- [ ] 5.2 Create weed-volume@.service template
- [ ] 5.3 Create weed-filer@.service template
- [ ] 5.4 Create weed-s3@.service template
- [ ] 5.5 Apply STIG-compliant hardening settings

## Phase 6: Configuration Management
- [ ] 6.1 Create /etc/default/weed/weed.conf template
- [ ] 6.2 Create startup script to read config and enable instances
- [ ] 6.3 Create example override configs (/etc/weed/master-1.toml, etc.)

## Phase 7: HAProxy Integration
- [ ] 7.1 Create /etc/haproxy/conf.d/weed-s3.cfg
- [ ] 7.2 Configure backend pool for S3 instances
- [ ] 7.3 Add health checks and round-robin balancing
- [ ] 7.4 Add postinst reload logic for haproxy

## Phase 8: Logging
- [ ] 8.1 Create /etc/logrotate.d/weed configuration
- [ ] 8.2 Ensure log directory ownership by weed user
- [ ] 8.3 Configure daily rotation, 14 days retention

## Phase 9: Artifact Management
- [ ] 9.1 Generate SHA256 checksums for all artifacts
- [ ] 9.2 Create GPG detached signatures
- [ ] 9.3 Archive deb packages, rpm packages, SBOMs, scan reports

## Phase 10: CI/CD Pipeline
- [ ] 10.1 Create .github/workflows/build.yml OR .gitlab-ci.yml
- [ ] 10.2 Implement tag detection trigger
- [ ] 10.3 Configure matrix build for all architectures
- [ ] 10.4 Add stage: Build → SBOM → Scan → Package → Sign → Archive

## Phase 11: Additional Enhancements
- [ ] 11.1 Create SELinux policy module for Oracle Linux
- [ ] 11.2 Create AppArmor profile for Ubuntu
- [ ] 11.3 Create /opt/weed/healthcheck.sh script
- [ ] 11.4 Create pre-flight validation tool
- [ ] 11.5 Add port conflict detection
- [ ] 11.6 Configure graceful shutdown support
- [ ] 11.7 Add systemd watchdog integration
- [ ] 11.8 Set immutable binary permissions (chmod 0755 root:root)

## Phase 12: Documentation
- [ ] 12.1 Document directory structure
- [ ] 12.2 Document signing instructions
- [ ] 12.3 Create example configuration files
- [ ] 12.4 Document compliance features
