Markdown
# Agente Conversacional com RAG — Direito Trabalhista Brasileiro

Projeto desenvolvido para o **Challenge Alura** no âmbito do programa **Algar: TFTI**. Trata-se de um assistente virtual inteligente baseado em **RAG (Retrieval-Augmented Generation)**, construído para responder a dúvidas e consultas sobre a legislação trabalhista brasileira (CLT) com fundamentação jurídica direta e precisa.

---

## 📌 Sumário
- [Sobre o Projeto](#-sobre-o-projeto)
- [Arquitetura RAG](#-arquitetura-rag)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Estrutura do Repositório](#-estrutura-do-repositório)
- [Instalação e Configuração](#-instalação-e-configuração)
- [Como Executar](#-como-executar)
- [Exemplo de Uso](#-exemplo-de-uso)
- [Autor](#-autor)

---

## 🚀 Sobre o Projeto

O objetivo do projeto é facilitar o acesso a informações trabalhistas de forma acessível e assertiva. Utilizando a técnica de RAG, o agente recupera trechos atualizados da CLT e normas complementares antes de elaborar a resposta, garantindo acurácia e mitigando alucinações de modelos de linguagem generativa.

### Principais Destaques:
- **Respostas Fundamentadas:** Citação explicita dos artigos da CLT referentes às dúvidas enviadas.
- **Busca Semântica:** Uso de banco vetorial para encontrar a legislação relevante mesmo com variações na linguagem do usuário.
- **Integração em Pipeline:** Processamento automatizado de documentos, indexação vetorial e geração de respostas em linguagem natural.

---

## ⚙️ Arquitetura RAG

┌───────────────────────────┐      ┌───────────────────────────┐
│     Pergunta do Usuário   │      │   Base Legal (CLT/PDFs)   │
└─────────────┬─────────────┘      └─────────────┬─────────────┘
│                                  │ (Ingestão / Chunking)
▼                                  ▼
┌───────────────────────────┐      ┌───────────────────────────┐
│    Embedding da Pergunta  │      │  Banco Vetorial (Chroma)  │
└─────────────┬─────────────┘      └─────────────┬─────────────┘
│                                  │
└──────────────┬───────────────────┘
│ (Busca Semântica)
▼
┌─────────────────────────────┐
│    Contexto Relevante       │
└──────────────┬──────────────┘
│
▼
┌─────────────────────────────┐
│    Modelo de IA (Prompt)    │
└──────────────┬──────────────┘
│
▼
┌─────────────────────────────┐
│ Resposta Final Fundamentada │
└─────────────────────────────┘


---

## 🛠️ Tecnologias Utilizadas

- **Linguagem:** Python 3.10+
- **Orquestração de RAG:** LangChain / LlamaIndex
- **Modelos de Linguagem & Embeddings:** Google Gemini API / OpenAI API
- **Banco de Dados Vetorial:** ChromaDB / FAISS
- **Interface de Usuário:** Streamlit / Gradio / Jupyter Notebook

---

## 📂 Estrutura do Repositório

```text
├── data/                    # Documentos da CLT e legislação de apoio (PDF/TXT)
├── vectorstore/             # Diretório do banco vetorial persistido
├── src/
│   ├── ingestion.py         # Leitura, divisão de texto (chunking) e geração de embeddings
│   ├── retriever.py         # Módulo de busca semântica na base vetorial
│   └── agent.py             # Configuração do agente e do pipeline de prompt + LLM
├── app.py                   # Arquivo principal da aplicação / interface
├── requirements.txt         # Dependências do projeto
├── .env.example             # Modelo de arquivo com variáveis de ambiente
└── README.md                # Documentação do repositório
📋 Instalação e Configuração
1. Clonar o repositório
Bash
git clone [https://github.com/oscarnettu/Agente-Conversacional-com-RAG-Direito-Trabalhista-Brasileiro.git](https://github.com/oscarnettu/Agente-Conversacional-com-RAG-Direito-Trabalhista-Brasileiro.git)
cd Agente-Conversacional-com-RAG-Direito-Trabalhista-Brasileiro
2. Criar e ativar o ambiente virtual
Bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux / macOS
python3 -m venv venv
source venv/bin/activate
3. Instalar as dependências
Bash
pip install -r requirements.txt
4. Configurar as variáveis de ambiente
Crie um arquivo .env na raiz do projeto com base no .env.example:

Snippet de código
GOOGLE_API_KEY="SUA_CHAVE_API_AQUI"
💻 Como Executar
Ingestão dos dados e criação da base vetorial:

Bash
python src/ingestion.py
Início do Agente Conversacional:

Bash
streamlit run app.py
💬 Exemplo de Uso
Usuário: Qual é o prazo limite para o pagamento do décimo terceiro salário?

Agente:

De acordo com a Lei nº 4.749/1965, a primeira parcela do décimo terceiro salário deve ser paga entre os meses de fevereiro e o dia 30 de novembro de cada ano. A segunda parcela deve ser quitada até o dia 20 de dezembro.

👤 Autor
Desenvolvido por Oscar Netto para o Challenge Alura do programa Algar: TFTI.
