# Deploy to Agent Runtime with Agents CLI

<div class="language-support-tag" title="Agent Runtime currently supports Python and Go.">
    <span class="lst-supported">Supported in ADK</span><span class="lst-python">Python</span><span class="lst-go">Go v1.2.0</span>
</div>

[Agents CLI in Agent Platform](https://google.github.io/agents-cli/) adds a
container build, CI/CD pipelines, and Terraform configuration to an existing ADK
project, then deploys it to Agent Runtime. Review the generated configuration
against your organization's security and compliance standards before you deploy
to production.

For prerequisites and installation, see
[Getting started](https://google.github.io/agents-cli/guide/getting-started/).
For the IAM roles and credentials each deployment target needs, see
[Authentication](https://google.github.io/agents-cli/guide/authentication/).

## Add the deployment files

Run the following command from the parent directory that contains your agent
folder. Accept the default answers unless you need to change them, and choose
one of the
[supported regions](https://docs.cloud.google.com/agent-builder/locations#supported-regions-agent-engine)
for Agent Runtime:

```shell
agents-cli scaffold enhance --deployment-target agent_runtime
```

The command copies your project to `~/.agents-cli/backups` before it adds the
files needed for deployment.

## Deploy your agent

Agents CLI deploys to your current Google Cloud project. Confirm which project
that is:

```shell
gcloud config get-value project
```

Then build and deploy the agent:

```shell
agents-cli deploy
```

This command builds a container from your agent code, pushes the container to a
registry, and deploys it to Agent Runtime.

For deployment flags, deployment status, and the other supported targets, see
the
[Agents CLI deployment guide](https://google.github.io/agents-cli/guide/deployment/).

## Next steps

*   [Test deployed agents in Agent Runtime](/deploy/agent-runtime/test/) to
    confirm the deployed agent responds
*   [Observability](https://google.github.io/agents-cli/guide/observability/) to
    add prompt-response logging and content logs
*   [CI/CD and production](https://google.github.io/agents-cli/guide/cicd/) to
    automate staging and production deployments
