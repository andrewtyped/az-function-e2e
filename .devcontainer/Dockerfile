 #See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.191.0/containers/dotnetcore/.devcontainer/base.Dockerfile

# [Choice] .NET Core version: 6.0, 5.0, 3.1, 2.1
ARG VARIANT="6.0"
FROM mcr.microsoft.com/vscode/devcontainers/dotnet:${VARIANT}

ARG INSTALL_AZURE_FUNCTIONS_TOOLS="true"
RUN if [ "$INSTALL_AZURE_FUNCTIONS_TOOLS" = "true" ]; then curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg; sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg; sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-$(lsb_release -cs)-prod $(lsb_release -cs) main" > /etc/apt/sources.list.d/dotnetdev.list'; apt-get update && export DEBIAN_FRONTEND=noninteractive && apt-get -y install --no-install-recommends azure-functions-core-tools-4; fi

# Install az cli
RUN sudo sh -c 'curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash'

# Install Terraform
RUN apt-get update && apt-get install -y gnupg software-properties-common curl \
    && curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - \
    && sudo sh -c 'apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"' \
    && apt-get update && apt-get -y install --no-install-recommends terraform