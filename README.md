# awesome-software-supply-chain-security [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A compilation of resources in the software supply chain security domain, with emphasis on open source.

## About the categories

There is no prescribed taxonomy for this domain. This list will necessarily have some overlap with disciplines and categories such as DevSecOps and SCA. The [supply-chain-synthesis](https://github.com/AevaOnline/supply-chain-synthesis/) repo offers a long-form read on why that's the case, plus helpful pointers to understand and navigate it as it evolves.

For `awesome-software-supply-chain-security` we take the following high-level approach: different actors in the supply chain contribute **attestations** to the elements represented in the chain. In this process view, attestations are _emitted_, _augmented_ (e.g., during composition) and _verified_. (Another way to look at this was described [here](https://twitter.com/joshbressers/status/1477366321436319745) by Josh Bressers.)

Using this lens we can identify a large group of "subjects" (dependencies), distinct categories of "facts" (licenses or vulnerabilities) and the specific role of identity, provenance and build systems. This is the rationale behind the current headings, which are expected to evolve with the domain.

Other examples of the ongoing process to define the domain include [Add Bad Design as a supply chain scenario · Issue #249 · slsa-framework/slsa](https://github.com/slsa-framework/slsa/issues/249) and [How does SLSA fit into broader supply chain security? · Issue #276 · slsa-framework/slsa](https://github.com/slsa-framework/slsa/issues/276). [Check out this tweet from Aeva Black](https://twitter.com/aevavoom/status/1491479149227118597) with Dan Lorenc for another in-a-pinch view of a couple key projects.

## Dependency intelligence

> This section includes: package management, library management, dependency management, vendored dependency management, by-hash searches, package, library and dependency naming, library behavior labeling, library publishing, registries and repositories, publishing gates and scans, dependency lifecycle.

* [package-url/purl-spec: A minimal specification for purl aka. a package &quot;mostly universal&quot; URL, join the discussion at https://gitter.im/package-url/Lobby](https://github.com/package-url/purl-spec)
* Online services that help understand what a specific dependency _is_, or at least whether it's known (usually feeding it a package identifier, such as `purl`, CPE or another form of `ecosystem:name:version`, or alternatively via hash):
  * [NSRL](https://www.nist.gov/itl/ssd/software-quality-group/national-software-reference-library-nsrl/about-nsrl/library-contents): hashes for [COTS software](https://www.nist.gov/itl/ssd/software-quality-group/national-software-reference-library-nsrl/about-nsrl/library-contents), well-integrated in tooling from [sleuthkit/hfind](http://manpages.ubuntu.com/manpages/bionic/man1/hfind.1.html) to [nsrllookup](https://github.com/rjhansen/nsrllookup)
  * A source that can be queried via a public API (HTTP and DNS!) and can be more open source-aware is [CIRCL hashlookup](https://www.circl.lu/services/hashlookup/)
  * [Repology](https://repology.org/) has legendary coverage for Linux packages across multiple distribution; its [repology-updater](https://github.com/repology/repology-updater) and other infrastructure pieces are open source. It provides an updater for [WikiData](https://github.com/repology/repology-wikidata-bot) which also has properties of interest for the supply chain security domain.
  * Tidelift's [libraries.io](https://libraries.io/) provides an [API](https://libraries.io/api) and supports over 30 package ecosystems
  * WhiteSource's [Unified Agent](https://whitesource.atlassian.net/wiki/spaces/WD/pages/1140852201/Getting+Started+with+the+Unified+Agent#Binary-and-Source-File-Matching-Overview) also offers some sophisticated file matching abilities
  * The [Software Heritage Project](https://archive.softwareheritage.org/) has massive ingestion capabilities and [offers an API](https://archive.softwareheritage.org/api/1/known/doc/) which can efficiently check whether a hash is known, and provide certain information on the file if so
  * [ClearlyDefined](https://docs.clearlydefined.io/using-data) provides licensing information for open source components, given their coordinates
  * [LGTM - Code Analysis Platform to Find and Prevent Vulnerabilities](https://lgtm.com/#explore) allows manually searching by GitHub repo
* For inputs acquired e.g., via `curl`:
  * [SpectralOps/preflight: preflight helps you verify scripts and executables to mitigate chain of supply attacks such as the recent Codecov hack.](https://github.com/spectralops/preflight)
  * [apiaryio/curl-trace-parser: Parser for output from Curl --trace option](https://github.com/apiaryio/curl-trace-parser)
    * [curl trace attestor · Issue #139 · testifysec/witness](https://github.com/testifysec/witness/issues/139)
  * [Friends don't let friends Curl | Bash](https://sysdig.com/blog/friends-dont-let-friends-curl-bash/)
  * [Falco](https://falco.org/)
  * [aquasecurity/tracee: Linux Runtime Security and Forensics using eBPF](https://github.com/aquasecurity/tracee)
  * [genuinetools/bane: Custom &amp; better AppArmor profile generator for Docker containers.](https://github.com/genuinetools/bane)
  * [containers/oci-seccomp-bpf-hook: OCI hook to trace syscalls and generate a seccomp profile](https://github.com/containers/oci-seccomp-bpf-hook)
  * [bottlerocket-os/hotdog: Hotdog is a set of OCI hooks used to inject the Log4j Hot Patch into containers.](https://github.com/bottlerocket-os/hotdog)
* [deepfence/ThreatMapper: 🔥 🔥   Open source cloud native security observability platform. Linux, K8s, AWS Fargate and more. 🔥 🔥](https://github.com/deepfence/ThreatMapper)
* [dependency-check](https://jeremylong.github.io/DependencyCheck/index.html)
* [ossf/package-analysis: Open Source Package Analysis](https://github.com/ossf/package-analysis) and [ossf/package-feeds: Feed parsing for language package manager updates](https://github.com/ossf/package-feeds)
* [cugu/gocap: List your dependencies capabilities and monitor if updates require more  capabilities.](https://github.com/cugu/gocap)
* [Checkmarx/chainalert-github-action: scans popular packages and alerts in cases there is suspicion of an account takeover](https://github.com/Checkmarx/chainalert-github-action)

Also read:

* [TaptuIT/awesome-devsecops: Curating the best DevSecOps resources and tooling.](https://github.com/TaptuIT/awesome-devsecops#dependency-management)

### SCA and SBOM

> This section includes: package/library scanners and detectors, SBOM formats, standards, authoring and validation, and a few applications. Will likely include SCA.

The most complete reference is [awesomeSBOM/awesome-sbom](https://github.com/awesomeSBOM/awesome-sbom)

* [What an SBOM Can Do for You](https://blog.chainguard.dev/what-an-sbom-can-do-for-you/)
* [awesomeSBOM/awesome-sbom: A curated list of SBOM (Software Bill Of Materials) related tools, frameworks, blogs, podcasts, and articles](https://github.com/awesomeSBOM/awesome-sbom)
* OWASP's [SCA tools](https://owasp.org/www-community/Source_Code_Analysis_Tools) list is comprehensive on its own
* [Grafeas: A Component Metadata API](https://github.com/grafeas/grafeas)
* [trailofbits/it-depends: A tool to automatically build a dependency graph and Software Bill of Materials (SBOM) for packages and arbitrary source code repositories.](https://github.com/trailofbits/it-depends)
* [Whitesource Renovate: Automated Dependency Updates](https://www.whitesourcesoftware.com/free-developer-tools/renovate/)
* [JFrog Xray - Universal Component Analysis &amp; Container Security Scanning](https://jfrog.com/xray/)
* [DependencyTrack/dependency-track: Dependency-Track is an intelligent Component Analysis platform that allows organizations to identify and reduce risk in the software supply chain.](https://github.com/DependencyTrack/dependency-track)
* [anchore/syft: CLI tool and library for generating a Software Bill of Materials from container images and filesystems](https://github.com/anchore/syft) from [Software supply chain security solutions • Anchore](https://anchore.com/)
* [Container Security | Qualys, Inc.](https://www.qualys.com/apps/container-security/)
* [Aqua Cloud Native Security, Container Security &amp; Serverless Security](https://www.aquasec.com/)
* [tern-tools/tern: Tern is a software composition analysis tool and Python library that generates a Software Bill of Materials for container images and Dockerfiles. The SBOM that Tern generates will give you a layer-by-layer view of what&#39;s inside your container in a variety of formats including human-readable, JSON, HTML, SPDX and more.](https://github.com/tern-tools/tern)
* [REA-Products/C-SCRM-Use-Case at master · rjb4standards/REA-Products](https://github.com/rjb4standards/REA-Products/tree/master/C-SCRM-Use-Case) from [this tweet](https://twitter.com/rjb4standards/status/1481250447331573761?s=12)
* [peterjmorgan/phylum-analyze-pr-action: GitHub Action to analyze Pull Requests for open-source supply chain issues](https://github.com/peterjmorgan/phylum-analyze-pr-action) from [Phylum | Future of Software Supply Chain Security](https://phylum.io/)
* [OWASP/Software-Component-Verification-Standard: Software Component Verification Standard (SCVS)](https://github.com/OWASP/Software-Component-Verification-Standard)

### Vulnerability information exchange

* [CycloneDX - Vulnerability Exploitability Exchange (VEX)](https://cyclonedx.org/capabilities/vex/)
* [OSV](https://osv.dev/)
* Qualys' [Vulnerability Detection Pipeline](https://community.qualys.com/vulnerability-detection-pipeline/)
* [Vuls · Agentless Vulnerability Scanner for Linux/FreeBSD](https://vuls.io/)
* [aquasecurity/trivy: Scanner for vulnerabilities in container images, file systems, and Git repositories, as well as for configuration issues](https://github.com/aquasecurity/trivy)
* [cve-search/cve-search: cve-search - a tool to perform local searches for known vulnerabilities](https://github.com/cve-search/cve-search)
* [nexB/vulnerablecode: A work-in-progress towards a free and open vulnerabilities database and the packages they impact. And the tools to aggregate and correlate these vulnerabilities. Sponsored by NLnet https://nlnet.nl/project/vulnerabilitydatabase/ for https://www.aboutcode.org/ Chat at https://gitter.im/aboutcode-org/vulnerablecode](https://github.com/nexB/vulnerablecode)
* [toolswatch/vFeed: The Correlated CVE Vulnerability And Threat Intelligence Database API](https://github.com/toolswatch/vFeed)
* [ossf/scorecard: Security Scorecards - Security health metrics for Open Source](https://github.com/ossf/scorecard) and [ossf/security-reviews: A community collection of security reviews of open source software components.](https://github.com/ossf/security-reviews)
* [Lynis - Security auditing and hardening tool for Linux/Unix](https://cisofy.com/lynis/)
* [victims/victims-cve-db: CVE database store](https://github.com/victims/victims-cve-db)

## Point-of-use validations

> This section includes: admission and ingestion policies, pull-time verification and end-user verifications.

* [Kyverno](https://kyverno.io/)
* [ckotzbauer/sbom-operator: Catalogue all images of a Kubernetes cluster to multiple targets with Syft](https://github.com/ckotzbauer/sbom-operator)
* [ossf/allstar: GitHub App to set and enforce security policies](https://github.com/ossf/allstar)
* [Open Policy Agent](https://www.openpolicyagent.org/)
* [Conftest](https://www.conftest.dev/examples/) allows to write tests against structured configuration data using the Open Policy Agent Rego query language: [here's an example](https://github.com/open-policy-agent/conftest/blob/master/examples/docker/policy/commands.rego)
* Several [pre-commit](https://pre-commit.com/hooks.html) hooks allow vulnerability checking right before dependency ingestion time into the codebase
  * e.g., [pyupio/safety: Safety checks your installed dependencies for known security vulnerabilities](https://github.com/pyupio/safety)
    * Or [npm-audit](https://docs.npmjs.com/cli/v8/commands/npm-audit)
    * Or [requires.io | Monitor your dependencies](https://requires.io/)
    * Or [Brakeman Security Scanner](https://brakemanscanner.org/)
    * Or [trailofbits/pip-audit: Audits Python environments and dependency trees for known vulnerabilities](https://github.com/trailofbits/pip-audit)
* Static analysis is often used at this stage in order to detect dependency acquisition, e.g.:
  * [Semgrep](https://semgrep.dev/)
  * [graudit/signatures at master · wireghoul/graudit](https://github.com/wireghoul/graudit/tree/master/signatures)
  * [banyanops/collector: A framework for Static Analysis of Docker container images](https://github.com/banyanops/collector)
  * [quay/clair: Vulnerability Static Analysis for Containers](https://github.com/quay/clair)
  * [eliasgranderubio/dagda: a tool to perform static analysis of known vulnerabilities, trojans, viruses, malware &amp; other malicious threats in docker images/containers and to monitor the docker daemon and running docker containers for detecting anomalous activities](https://github.com/eliasgranderubio/dagda)
  * [KICS - Keeping Infrastructure as Code Secure](https://kics.io/)
  * [tinkerbell/lint-install: Consistently install reasonable linter rules for open-source projects](https://github.com/tinkerbell/lint-install)
  * `hadolint` rules on package installation, e.g., [hadolint/README.md at d16f342c8e70fcffc7a788d122a1ba602075250d · hadolint/hadolint](https://github.com/hadolint/hadolint/blob/d16f342c8e70fcffc7a788d122a1ba602075250d/README.md#rules)
    * Also [dockerfile resource scans - checkov](https://www.checkov.io/5.Policy%20Index/dockerfile.html) from [bridgecrewio/checkov: Prevent cloud misconfigurations during build-time for Terraform, CloudFormation, Kubernetes, Serverless framework and other infrastructure-as-code-languages with Checkov by Bridgecrew.](https://github.com/bridgecrewio/checkov)
* [Vulnerability Assessment | OpenSCAP portal](https://www.open-scap.org/features/vulnerability-assessment/)

Also see:

* [analysis-tools-dev/static-analysis: ⚙️ A curated list of static analysis (SAST) tools for all programming languages, config files, build tools, and more.](https://github.com/analysis-tools-dev/static-analysis/)
* [anderseknert/awesome-opa: A curated list of OPA related tools, frameworks and articles](https://github.com/anderseknert/awesome-opa)

## Identity, signing and provenance

> This section includes: projects and discussions specifics to developer identity, OIDC, keyrings and related topics.

* Part of [sigstore](https://www.sigstore.dev/)
    * [Cosign](https://docs.sigstore.dev/cosign/overview)
    * [Fulcio](https://docs.sigstore.dev/fulcio/overview)
    * [Rekor](https://docs.sigstore.dev/rekor/overview)
* [technosophos/helm-gpg: Chart signing and verification with GnuPG for Helm.](https://github.com/technosophos/helm-gpg)
* [notaryproject/notary: Notary is a project that allows anyone to have trust over arbitrary collections of data](https://github.com/notaryproject/notary)
  * [notaryproject/roadmap: Roadmap for NotaryV2](https://github.com/notaryproject/roadmap)
  * [notaryproject/notation: Notation is a project to add signatures as standard items in the registry ecosystem, and to build a set of simple tooling for signing and verifying these signatures. Based on Notary V2 standard.](https://github.com/notaryproject/notation)
  * [notaryproject/tuf: The Update Framework for OCI Registries](https://github.com/notaryproject/tuf)
    * Also see [vmware-labs/repository-editor-for-tuf: Command line tool for editing and maintaining a TUF repository](https://github.com/vmware-labs/repository-editor-for-tuf)
    * Also see [How to easily try out TUF + in-toto](https://badhomb.re/ci/security/2020/05/01/tuf-in-toto.html)
* [deislabs/ratify: Artifact Ratification Framework](https://github.com/deislabs/ratify)
* [latchset/tang: Tang binding daemon](https://github.com/latchset/tang)
* [An exposed apt signing key and how to improve apt security](https://blog.cloudflare.com/dont-use-apt-key/)
* See [Issue #21 · testifysec/witness](https://github.com/testifysec/witness/issues/21#issuecomment-991774080) for a succinct description of how [testifysec/witness: Witness is a pluggable framework for software supply chain risk management.  It automates, normalizes, and verifies software artifact providence.](https://github.com/testifysec/witness/) deals with attestation chains 
* The _Supply Chain Risk Management_ section of [SP 800-53 Rev. 5, Security and Privacy Controls for Info Systems and Organizations | CSRC](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final), also see [center-for-threat-informed-defense/attack-control-framework-mappings: Security control framework mappings to MITRE ATT&CK](https://github.com/center-for-threat-informed-defense/attack-control-framework-mappings)

## Frameworks and best practice references

> This section includes: reference architectures and authoritative compilations of supply chain attacks and the emerging categories.

* [in-toto | A framework to secure the integrity of software supply chains](https://in-toto.io/)
* [Supply chain Levels for Software Artifacts](https://slsa.dev/) or SLSA (salsa) is a security framework, a check-list of standards and controls to prevent tampering, improve integrity, and secure packages and infrastructure in your projects, businesses or enterprises. 
* [OWASP Application Security Verification Standard](https://owasp.org/www-project-application-security-verification-standard/), esp. _V14 - Configuration_
* SAFECODE's [Fundamental Practices for Secure Software Development, Third Edition](https://safecode.org/uncategorized/fundamental-practices-secure-software-development/), esp. _Manage Security Risk Inherent in the Use of Third-party Components_
* [SSF | The Secure Software Factory](https://thesecuresoftwarefactory.github.io/ssf/) and [mlieberman85/supply-chain-examples](https://github.com/mlieberman85/supply-chain-examples)
* [Software Supply Chain Risk Management | BSIMM](https://www.bsimm.com/about/bsimm-for-vendors.html)
* [microsoft/scim: Supply Chain Integrity Model](https://github.com/microsoft/SCIM)

## Build techniques

> This section includes: reproducible builds, hermetic builds, bootstrappable builds, special considerations for CI/CD systems, best practices building artifacts such as OCI containers, etc.

* [Reproducible Builds](https://reproducible-builds.org/), particularly the [Documentation](https://reproducible-builds.org/docs/)
* [Bootstrappable Builds (GNU Mes Reference Manual)](https://www.gnu.org/software/mes/manual/html_node/Bootstrappable-Builds.html)
  * Also read [Bootstrappable builds](https://lwn.net/Articles/841797/) from LWN
* [kpcyrd/pacman-bintrans: Experimental binary transparency for pacman with sigstore and rekor](https://github.com/kpcyrd/pacman-bintrans)
* [fepitre/package-rebuilder: Standalone orchestrator for rebuilding Debian, Fedora and Qubes OS packages in order to generate `in-toto` metadata which can be used with `apt-transport-in-toto` or `dnf-plugin-in-toto` to validate reproducible status.](https://github.com/fepitre/package-rebuilder)
* [kpcyrd/rebuilderd-debian-buildinfo-crawler: Reproducible Builds: Scraper/Parser for https://buildinfos.debian.net into structured data](https://github.com/kpcyrd/rebuilderd-debian-buildinfo-crawler)
  * Also see [Reproducible Builds: Debian and the case of the missing version string - vulns.xyz](https://vulns.xyz/2022/01/debian-missing-version-string/)
* [kpcyrd/rebuilderd: Independent verification of binary packages - reproducible builds](https://github.com/kpcyrd/rebuilderd)

Also see:

* The [reproducible-builds](https://github.com/topics/reproducible-builds) topic on GitHub

## Talks, articles, media coverage and other reading

* [“Chain”ging the Game - how runtime makes your supply chain even more secure](https://sysdig.com/blog/chainging-the-game/)
* [How to attack cloud infrastructure via a malicious pull request](https://goteleport.com/blog/hack-via-pull-request/)
* The [Technology](https://snyk.io/series/devsecops/technology/) chapter in Snyk's DevSecOps series
* [The Challenges of Securing the Open Source Supply Chain](https://thenewstack.io/the-challenges-of-securing-the-open-source-supply-chain/)
* [What is a Software Supply Chain Attestation - and why do I need it?](https://www.testifysec.com/blog/what-is-a-supply-chain-attestation/)
* [Open Policy Agent 2021, Year in Review](https://blog.openpolicyagent.org/open-policy-agent-2021-year-in-review-f334244868e0)
* [What is VEX and What Does it Have to Do with SBOMs?](https://blog.adolus.com/what-is-vex-and-what-does-it-have-to-do-with-sboms)
* [What is VEX? It's the Vulnerability Exploitability eXchange!](https://zt.dev/posts/what-is-vex/)
* [Buildpacks and SBOM Integration Opportunities](https://zt.dev/posts/buildpacks-sbom-opportunities/)
* [The state of software bill of materials: SBOM growth could bolster software supply chains](https://venturebeat.com/2022/02/02/the-state-of-software-bill-of-materials-sbom-growth-could-bolster-software-supply-chains/)
* A helpful list of acronyms: [Acronyms | OpenSCAP portal](https://www.open-scap.org/resources/acronyms/)
* [slsa/terminology.md at main · slsa-framework/slsa](https://github.com/slsa-framework/slsa/blob/main/docs/_spec/v0.1/terminology.md)
* [Secure Your Software Supply Chain with New VMware Tanzu Application Platform Capabilities](https://tanzu.vmware.com/content/blog/secure-software-supply-chain-vmware-tanzu-application-platform)
  * [Secure Software Supply Chains](https://tanzu.vmware.com/developer/learningpaths/secure-software-supply-chain/)
* A few resources to understand supply chain compromises:
  * [Supply Chain Compromise - attackics](https://collaborate.mitre.org/attackics/index.php/Technique/T0862#:~:text=Supply%20chain%20compromise%20is%20the,receipt%20by%20the%20end%20consumer.&text=This%20may%20involve%20the%20compromise,third%20party%20or%20vendor%20websites.)
  * [tag-security/supply-chain-security/compromises at main · cncf/tag-security](https://github.com/cncf/tag-security/tree/main/supply-chain-security/compromises)
  * [IQTLabs/software-supply-chain-compromises: A dataset of software supply chain compromises. Please help us maintain it!](https://github.com/IQTLabs/software-supply-chain-compromises)
  * Also follow: [Publish list of OSS compromises and how SLSA can help · Issue #222 · slsa-framework/slsa](https://github.com/slsa-framework/slsa/issues/222#issuecomment-1030356313) and watch [ossf/oss-compromises](https://github.com/ossf/oss-compromises)
* [Improving TOFU (trust on first use) With Transparency](https://dlorenc.medium.com/improving-tofu-with-transparency-da674aa2879d)
* Reports:
  * [2022 State of Cloud Native Security Report - Palo Alto Networks](https://www.paloaltonetworks.com/state-of-cloud-native-security)
* End-to-end demos and examples:
  * [goreleaser/supply-chain-example: Example goreleaser + github actions config with keyless signing and SBOM generation](https://github.com/goreleaser/supply-chain-example)