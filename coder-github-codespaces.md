## Comparison: Coder vs GitHub Codespaces

### **Core Philosophy**

**Coder:**
- Self-hosted platform you run on **your infrastructure**
- Full control over where workspaces run (cloud, on-prem, hybrid)
- Infrastructure-as-Code approach using **Terraform**
- Open-source (AGPL-3.0) with premium features

**GitHub Codespaces:**
- **GitHub-managed SaaS** running on Azure infrastructure
- Zero infrastructure management — fully hosted by GitHub
- Configuration via **devcontainer.json** (Dev Container spec)
- Integrated tightly with GitHub repositories

### **Hosting & Control**

**Coder:**
- ✅ **You own the infrastructure** — runs in your cloud/datacenter
- ✅ Data never leaves your environment
- ✅ Choose any cloud provider or on-premises
- ✅ Complete control over security, compliance, networking
- ⚠️ You manage the control plane (installation, updates, maintenance)

**GitHub Codespaces:**
- ✅ **Zero infrastructure management** — GitHub handles everything
- ✅ Instant availability, no setup required
- ⚠️ Runs on **GitHub's Azure infrastructure** only
- ⚠️ Code and data reside on Microsoft/GitHub servers
- ⚠️ Limited control over underlying infrastructure

### **Infrastructure Flexibility**

**Coder:**
- ✅ Provision **any compute**: VMs, containers, Kubernetes pods, bare metal
- ✅ AWS, GCP, Azure, DigitalOcean, on-prem, hybrid cloud
- ✅ Mix infrastructure types per team/project
- ✅ Use spot instances, reserved instances for cost optimization
- ✅ Define complex multi-VM/multi-service environments

**GitHub Codespaces:**
- ⚠️ **Container-based only** (Linux containers)
- ⚠️ Fixed machine types: 2-core to 32-core options
- ⚠️ Runs exclusively on GitHub's Azure infrastructure
- ⚠️ Cannot use your existing cloud accounts or on-prem resources

### **IDE Experience**

**Coder:**
- ✅ **Native desktop IDEs**: VS Code Remote SSH, JetBrains Gateway
- ✅ Browser-based: code-server (VS Code fork)
- ✅ Any SSH-compatible tool
- ✅ Use **full VS Code marketplace** (not restricted)
- ✅ Traditional SSH access

**GitHub Codespaces:**
- ✅ **VS Code in browser** (primary experience)
- ✅ Connect from **VS Code desktop** (via extension)
- ✅ JetBrains Gateway support
- ⚠️ Browser-first experience (desktop connection is secondary)
- ⚠️ Uses **Open VSX registry** for extensions (not full VS Code marketplace)

### **GitHub Integration**

**Coder:**
- ✅ Works with **any Git provider** (GitHub, GitLab, Bitbucket, self-hosted)
- ✅ Not tied to GitHub
- ⚠️ Requires separate configuration for Git auth

**GitHub Codespaces:**
- ✅ **Native GitHub integration** — one-click from repo, PR, or issue
- ✅ Automatic GitHub authentication
- ✅ Built into GitHub UI/workflow
- ✅ "Open in Codespace" button everywhere
- ⚠️ **GitHub repositories only** — cannot use with GitLab, Bitbucket, etc.

### **Pricing Model**

**Coder:**
- ✅ **Pay your cloud provider directly** for compute/storage
- ✅ Control costs via Terraform (auto-shutdown, spot instances)
- ✅ Coder software is open-source (free) or premium (paid seat licenses)
- ✅ Predictable enterprise pricing
- ✅ No per-hour usage fees from Coder

**GitHub Codespaces:**
- **Usage-based billing** through GitHub:
  - **Compute**: ~$0.18/hour (2-core) to $3.60/hour (32-core)
  - **Storage**: ~$0.07/GB-month
  - **Free tier**: 120 core-hours/month + 15GB storage (Pro/Team plans)
- ⚠️ Costs can accumulate quickly for heavy usage
- ⚠️ Billing managed by GitHub, not directly by you
- ⚠️ Less control over cost optimization (no spot instances, etc.)

### **Configuration Management**

**Coder:**
- **Terraform templates** define entire workspace infrastructure
- Admins control templates; developers create workspaces from templates
- Version control templates like code
- Can include complex networking, multiple VMs, databases, etc.

**GitHub Codespaces:**
- **devcontainer.json** defines container configuration
- Per-repository configuration (committed to repo)
- Pre-build feature for faster startup
- Limited to single-container or docker-compose setups
- Cannot provision external infrastructure (VMs, databases, etc.)

### **Free Tier**

**Coder:**
- ⚠️ No free tier (you pay cloud provider for infrastructure)
- ✅ Open-source software is free to use
- ⚠️ Must set up and maintain control plane

**GitHub Codespaces:**
- ✅ **60 hours/month free** on 2-core machine (personal accounts)
- ✅ **120 core-hours/month free** with GitHub Pro/Team/Enterprise
- ✅ 15GB free storage
- ✅ Perfect for trying out or light usage

### **Enterprise Features**

**Coder:**
- RBAC, audit logs, quotas
- SSO/SAML integration
- Air-gapped deployment support
- Custom branding
- High availability configurations

**GitHub Codespaces:**
- Enterprise policy controls (machine type limits, retention)
- Organizational billing
- Pre-build management
- Integration with GitHub Advanced Security
- SSO via GitHub Enterprise

### **Developer Onboarding**

**Coder:**
- Click workspace URL → Terraform provisions infrastructure → connect via IDE
- Time: seconds to minutes (depending on infrastructure)
- Admins must create/maintain templates

**GitHub Codespaces:**
- Click "Code" → "Create codespace" → environment ready in ~30 seconds
- Zero admin setup for basic use (uses default devcontainer)
- Can customize with devcontainer.json

### **Network & Security**

**Coder:**
- ✅ Runs **inside your network** perimeter
- ✅ WireGuard tunnel for secure connections
- ✅ Full control over firewall rules, VPCs, private networks
- ✅ Air-gapped deployments possible

**GitHub Codespaces:**
- ⚠️ Runs on **GitHub's infrastructure** (Azure)
- ⚠️ Code/data on Microsoft servers
- ✅ SOC 2, ISO 27001 compliance
- ⚠️ Cannot run in air-gapped environments

### **Use Cases**

**Coder is better for:**
- Organizations requiring **data sovereignty**
- Regulated industries (healthcare, finance, government)
- Companies with existing cloud infrastructure
- Teams needing **VM-based or complex environments**
- Air-gapped or on-premises requirements
- Multi-cloud strategies
- Cost-sensitive teams with high usage
- Non-GitHub workflows (GitLab, Bitbucket, etc.)

**GitHub Codespaces is better for:**
- Teams **deeply integrated with GitHub**
- Startups wanting zero infrastructure management
- Open-source projects on GitHub
- Quick prototyping and demos
- Remote contributors needing instant access
- Teams comfortable with SaaS/cloud dependencies
- Light to moderate usage (free tier friendly)
- Reviewing PRs in isolated environments

### **Key Trade-offs**

| Factor | Coder | GitHub Codespaces |
|--------|-------|-------------------|
| **Control** | Full control, you manage | Zero management, GitHub controls |
| **Flexibility** | Any infrastructure | Containers on Azure only |
| **Cost model** | Cloud bills + licensing | Usage-based through GitHub |
| **Setup effort** | Requires installation | Instant, no setup |
| **Data location** | Your infrastructure | GitHub/Microsoft servers |
| **Git provider** | Any (GitHub, GitLab, etc.) | GitHub only |
| **IDE choice** | Native desktop preferred | Browser-first |

### **Bottom Line**

**Coder** is for organizations that need **infrastructure control, data sovereignty, and flexibility** to run workspaces anywhere. It requires more setup but provides maximum control.

**GitHub Codespaces** is for teams that want **zero infrastructure management** and are comfortable with a **GitHub-hosted SaaS solution**. It's the fastest path from "nothing" to "coding" but locks you into GitHub's infrastructure.
