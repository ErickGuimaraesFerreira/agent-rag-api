# 🧠 Agente RAG de PDF com Memória & API

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)
![Agno](https://img.shields.io/badge/Agno-Framework-orange?style=for-the-badge)
![Gemini](https://img.shields.io/badge/Google%20Gemini-AI-4285F4?style=for-the-badge&logo=google)
![Render](https://img.shields.io/badge/Deploy-Render-black?style=for-the-badge&logo=render)

Um Agente de IA profissional construído com **Agno** (anteriormente Phidata) que utiliza **RAG (Retrieval-Augmented Generation)** para responder perguntas de forma inteligente com base em documentos PDF. O projeto conta com **memória persistente**, permitindo lembrar preferências do usuário e interações passadas, e expõe uma API RESTful para fácil integração.

Atualmente configurado para analisar relatórios financeiros (ex: Grendene 2T25), mas facilmente adaptável para qualquer base de conhecimento.

---

## 🚀 Funcionalidades Principais

*   **📚 RAG (Geração Aumentada por Recuperação):** Ingere e indexa documentos PDF em um Banco de Dados Vetorial (ChromaDB) para respostas precisas e conscientes do contexto.
*   **🧠 Memória Persistente:** Usa SQLite para armazenar o histórico da sessão e memórias do usuário, permitindo interações personalizadas (ex: lembrar de chamar o usuário de "Senhor").
*   **⚡ LLM de Alta Performance:** Impulsionado pelo **Gemini 2.5 Flash** do Google para inferência rápida e econômica.
*   **🔌 API Pronta para Uso:** Servidor FastAPI integrado via `AgentOS` para servir os endpoints do agente.
*   **☁️ Pronto para Render:** Configurado para deploy contínuo no Render.com.

## 🛠️ Stack Tecnológica

*   **Framework:** [Agno](https://github.com/agno-agi/agno)
*   **LLM & Embeddings:** Google Gemini
*   **Banco de Dados Vetorial:** ChromaDB (Persistente)
*   **Banco de Dados:** SQLite (Armazenamento de sessão)
*   **Gerenciador de Pacotes:** uv / pip

---

## ⚙️ Instalação e Configuração

### Pré-requisitos
*   Python 3.9+
*   Chave de API do Google AI Studio

### 1. Clonar o Repositório
```bash
git clone https://github.com/seu-usuario/nome-do-repo.git
cd nome-do-repo
```

### 2. Configurar o Ambiente
Crie um arquivo `.env` na raiz do projeto:
```env
GOOGLE_API_KEY=sua_chave_api_google_aqui
```

### 3. Instalar Dependências
Usando `pip`:
```bash
pip install -r requirements.txt
```
Ou usando `uv` (recomendado pela velocidade):
```bash
uv pip install -r requirements.txt
```

---

## 🏃 Como Usar

### Executando Localmente
Inicie o servidor do agente:
```bash
python rag.py
```
A API estará disponível em `http://localhost:10000`. Você pode interagir com o agente através do playground do Agno ou chamadas diretas à API.

### Base de Conhecimento
O agente atualmente ingere o seguinte documento na inicialização:
*   *Grendene - Relatório Trimestral 2T25*

Para adicionar seus próprios PDFs, modifique a seção `knowledge.add_content` no arquivo `rag.py`.

---

## ☁️ Deploy no Render

Este projeto está configurado para rodar no [Render](https://render.com).

1.  **Crie um Web Service** no Render conectado ao seu repositório GitHub.
2.  **Build Command:** `pip install -r requirements.txt`
3.  **Start Command:** `python rag.py`
4.  **Variáveis de Ambiente:** Adicione `GOOGLE_API_KEY` no painel do Render.
5.  **Disco Persistente (Opcional mas Recomendado):** Monte um disco em `/opt/render/project/src/tmp` se desejar persistir o ChromaDB e o banco de dados SQLite entre reinicializações.

---

## 🤝 Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para enviar um Pull Request.

## 📄 Licença

Este projeto está licenciado sob a Licença MIT.
