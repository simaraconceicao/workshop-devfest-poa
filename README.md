# 🤖 Workshop DevFest POA - Agente de Portfólio GitHub

Este repositório contém o código desenvolvido durante o **Workshop do DevFest POA**. O projeto demonstra como criar um Agente de IA autônomo utilizando o **Google ADK (Agent Development Kit)**, o modelo **Gemini 3** e o **Remote GitHub MCP Server** para automatizar a gestão de portfólios e repositórios.

O deploy da aplicação é feito de forma escalável utilizando o **Google Cloud Run**.

## 🎤 Slides da Apresentação

Acompanhe o material visual e os slides utilizados durante o workshop:
👉 **[Visualizar Slides no Canva](https://www.canva.com/design/DAG6jSUVkgk/fIavaj_XRLzMJYB277FYTw/edit?utm_content=DAG6jSUVkgk&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)**

## 📚 Tecnologias e Documentação

*   **[Google ADK](https://google.github.io/adk-docs/)**: Unidade de execução autônoma para criar agentes que utilizam ferramentas externas e raciocínio inteligente.
*   **[Remote GitHub MCP Server](https://github.com/github/github-mcp-server)**: Protocolo que permite ao agente interagir diretamente com o GitHub (hosted by GitHub).
*   **[Google Cloud Run](https://cloud.google.com/run?hl=pt_br)**: Plataforma para executar o agente sem gerenciar infraestrutura.

## 🚀 Passo a Passo

### 1. Pré-requisitos
*   **Python 3.10** ou superior.
*   **Google Cloud Platform**: Projeto criado com conta de faturamento ativa e as seguintes APIs habilitadas:
    *   Vertex AI API
    *   Artifact Registry
    *   Cloud Run Admin API
*   **Chaves de Acesso** (⚠️ **Importante:** Mantenha suas chaves seguras e nunca as commite no repositório):
    *   **Gemini API Key**: Gere sua chave no [Google AI Studio](https://aistudio.google.com/api-keys).
    *   **GitHub PAT**: Crie um Personal Access Token nas [configurações do GitHub](https://github.com/settings/tokens).

### 2. Instalação e Execução Local

Instale a biblioteca do ADK:
```bash
pip install google-adk
```

Para rodar a interface web do agente localmente (na raiz do projeto):
```bash
adk web
```

### 3. Deploy no Google Cloud Run

Autentique-se no Google Cloud via terminal:
```bash
gcloud auth login
```

Configure as variáveis de ambiente necessárias (substitua pelos seus dados):
```bash
export AGENT_PATH="./my_agent"
export SERVICE_NAME="workshop-agent-devfest"
export GOOGLE_API_KEY="sua-chave-do-ai-studio"
export GOOGLE_GENAI_USE_VERTEXAI=FALSE
export GOOGLE_CLOUD_LOCATION="us-central1"
export GOOGLE_CLOUD_PROJECT="seu-id-do-projeto-gcp"
export GITHUB_PAT="seu-token-github"
```

Execute o comando de deploy do ADK:
```bash
adk deploy cloud_run \
--project=$GOOGLE_CLOUD_PROJECT \
--region=$GOOGLE_CLOUD_LOCATION \
--service_name=$SERVICE_NAME \
--with_ui \
$AGENT_PATH
```
