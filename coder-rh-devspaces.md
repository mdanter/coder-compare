## Executive Summary: Coder vs Red Hat OpenShift Dev Spaces

### Core Difference
**Coder** provisions development environments on any infrastructure using Terraform. **OpenShift Dev Spaces** runs containerized workspaces exclusively on Red Hat OpenShift using Kubernetes.

### Key Advantages

**Coder:**
- **Infrastructure flexibility** — AWS, GCP, Azure, on-prem, any Kubernetes, VMs, or containers
- **IDE freedom** — native desktop IDEs (VS Code, JetBrains) via SSH, not just browser
- **Cost control** — automatic shutdown, spot instances, granular per-workspace cost management
- **Multi-cloud ready** — no vendor lock-in

**OpenShift Dev Spaces:**
- **Turnkey for OpenShift** — included with subscription, operator-based installation
- **Enterprise integration** — built-in OpenShift OAuth, RBAC, Red Hat support/SLAs
- **Zero local setup** — fully browser-based, works on any device with a browser
- **RHEL security** — enterprise-hardened container images

### Decision Factors

| Choose Coder if you... | Choose Dev Spaces if you... |
|------------------------|----------------------------|
| Need multi-cloud or hybrid infrastructure | Are standardized on OpenShift |
| Want VM-based or mixed environments | Need pure container/Kubernetes workflows |
| Prefer native desktop IDEs | Prefer browser-only development |
| Require Terraform infrastructure control | Want Red Hat enterprise support |
| Have cost optimization as priority | Are already in Red Hat ecosystem |

### Bottom Line
Coder offers **maximum flexibility** across infrastructure and tools. OpenShift Dev Spaces offers **deep OpenShift integration** with enterprise support. The choice depends on your infrastructure strategy: infrastructure-agnostic (Coder) or OpenShift-committed (Dev Spaces).




## Comparison: Coder vs Red Hat OpenShift Dev Spaces

### **Architecture & Foundation**

**Coder:**
- Self-hosted platform for provisioning cloud development environments
- Infrastructure-as-Code approach using **Terraform** to define workspaces
- Can provision on **any infrastructure**: AWS EC2, GCP, Azure, Kubernetes pods, Docker containers, bare metal, etc.
- Written in **Go**, open-source (AGPL-3.0 license)
- Uses **WireGuard tunnel** for secure, high-speed connections to workspaces

**OpenShift Dev Spaces:**
- **Kubernetes-native** platform built on Eclipse Che
- Specifically designed for **OpenShift** (runs via OperatorHub)
- Workspaces defined using **devfile** format (declarative YAML)
- Tightly integrated with OpenShift's OAuth, RBAC, and networking
- Container-based workspaces managed by DevWorkspace Operator

### **Infrastructure Flexibility**

**Coder:**
- ✅ **Multi-cloud/multi-platform**: Run workspaces anywhere Terraform can provision
- ✅ Works with any Kubernetes distribution, VMs, containers, or physical servers
- ✅ Not locked to specific cloud provider or orchestrator
- ✅ Can mix infrastructure types (e.g., some devs on AWS, others on-prem)

**OpenShift Dev Spaces:**
- ⚠️ **OpenShift-specific**: Requires OpenShift Container Platform, OpenShift Dedicated, or ROSA
- ⚠️ Cannot run on vanilla Kubernetes or other platforms
- ⚠️ Tightly coupled to Red Hat ecosystem

### **IDE Support**

**Coder:**
- ✅ **Any IDE**: VS Code Remote, JetBrains Gateway, SSH, Web IDEs
- ✅ Native desktop IDE experience via SSH tunneling
- ✅ Support for browser-based code-server (VS Code fork)
- ✅ Developers can use their existing local IDE setup

**OpenShift Dev Spaces:**
- ✅ **VS Code - Open Source** (browser-based, default)
- ✅ **JetBrains IntelliJ IDEA** (browser-based, tech preview)
- ⚠️ Limited to browser-based IDEs
- ⚠️ Uses Open VSX registry (not official VS Code marketplace)
- ⚠️ Fewer extensions available compared to full VS Code

### **Workspace Provisioning**

**Coder:**
- Terraform templates define entire infrastructure stack
- Automatic **idle shutdown** to save costs
- Can provision complex multi-VM/multi-container setups
- Admin controls resource limits via Terraform

**OpenShift Dev Spaces:**
- Devfile describes workspace configuration (runtime, tools, IDE)
- Kubernetes pods manage workspace components
- Automatic idle timeout (configurable by admin)
- Resource limits set via Kubernetes resource quotas

### **Developer Onboarding**

**Coder:**
- Click URL → provision workspace from Terraform template
- Developers get full infrastructure (not just containers)
- Onboarding time: seconds to minutes (depending on infrastructure)

**OpenShift Dev Spaces:**
- Click URL → start workspace from devfile
- "Get Started" dashboard with sample stacks
- Badge support for "contribute to this repo" buttons
- Onboarding time: typically seconds (containerized)

### **Security & Enterprise Features**

**Coder:**
- Self-hosted control plane
- Enterprise features: RBAC, audit logs, group sync, workspace quotas
- Works within your VPC/network
- SSH key management

**OpenShift Dev Spaces:**
- Integrated with **OpenShift OAuth**
- Enterprise proxy and TLS certificate support
- RBAC via Kubernetes/OpenShift
- Code stays within organization network
- RHEL-based images (security-focused)

### **Cost Management**

**Coder:**
- ✅ Automatic shutdown of idle workspaces
- ✅ Works with spot/preemptible instances
- ✅ Fine-grained control over instance types
- ✅ Cost visibility via cloud provider

**OpenShift Dev Spaces:**
- ⚠️ Cost depends on OpenShift cluster sizing
- ⚠️ Less granular control over per-workspace costs
- Workspace idle timeout reduces resource usage

### **Use Cases**

**Coder is better for:**
- Organizations wanting infrastructure flexibility
- Multi-cloud or hybrid cloud environments
- Teams needing VMs or specific hardware
- Companies already using Terraform
- Scenarios requiring native desktop IDE experience
- Cost-sensitive teams (granular shutdown, spot instances)

**OpenShift Dev Spaces is better for:**
- Organizations standardized on OpenShift
- Teams already using Red Hat ecosystem
- Pure Kubernetes-native workflows
- Companies wanting Red Hat support/licensing
- Browser-only development requirements
- Organizations prioritizing RHEL security posture

### **Licensing & Support**

**Coder:**
- Open-source (AGPL-3.0)
- Premium features available (paid)
- Community support via Discord/GitHub
- Professional support available

**OpenShift Dev Spaces:**
- Included with OpenShift subscription
- Red Hat support and SLAs
- Product releases lag Eclipse Che by ~2 versions
- More "stable" than upstream Eclipse Che

### **Key Differentiator**

**Coder** = "Workspaces as Infrastructure" — use Terraform to provision any compute resource  
**OpenShift Dev Spaces** = "Workspaces as Kubernetes Pods" — container-native, OpenShift-only

Coder prioritizes flexibility and infrastructure choice; OpenShift Dev Spaces prioritizes OpenShift integration and containerized consistency.
