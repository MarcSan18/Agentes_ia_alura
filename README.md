
Projeto de Triagem de Service Desk com Langchain e Google Gemini

Este projeto demonstra a criação de um sistema simples de triagem automática para Service Desk utilizando a biblioteca Langchain e o modelo Google Gemini 2.5 Flash. O objetivo é classificar as mensagens dos usuários em categorias como AUTO_RESOLVER, PEDIR_INFO ou ABRIR_CHAMADO, além de determinar a urgência e identificar campos faltantes. Ele também implementa um sistema básico de Retrieval-Augmented Generation (RAG) para responder a perguntas baseadas em documentos de políticas internas.

Nota: Este projeto ainda está em desenvolvimento e pode sofrer alterações.

Funcionalidades
Classificação automática de mensagens de Service Desk (AUTO_RESOLVER, PEDIR_INFO, ABRIR_CHAMADO).
Definição de regras de triagem através de um prompt.
Saída estruturada em formato JSON utilizando Pydantic.
Integração com o modelo Google Gemini 2.5 Flash para triagem e respostas RAG.
Carregamento e processamento de documentos PDF para base de conhecimento.
Criação de embeddings e armazenamento em um banco de dados vetorial (FAISS).
Sistema de Retrieval-Augmented Generation (RAG) para responder perguntas com base nos documentos carregados.
Como usar
Instalar dependências: Execute a célula com pip install para instalar as bibliotecas necessárias.
Configurar a API Key: Obtenha uma chave de API do Google Gemini (Google AI Studio) e adicione-a aos segredos do Colab com o nome GEMINI_API_KEY. A célula que carrega a chave já está configurada para usar este nome.
Carregar Documentos: Adicione os arquivos PDF das políticas internas na pasta /content/ do ambiente Colab. Execute a célula que carrega os documentos usando PyMuPDFLoader.
Dividir Documentos: Execute a célula que utiliza RecursiveCharacterTextSplitter para dividir os documentos em pedaços menores (chunks).
Criar Embeddings e Vector Store: Execute as células que criam as embeddings usando GoogleGenerativeAIEmbeddings e, em seguida, a célula que cria o banco de dados vetorial FAISS a partir dos chunks e embeddings. Certifique-se de que não há erros de cota nesta etapa.
Configurar Cadeias Langchain: Execute as células que definem os prompts e criam as cadeias Langchain (llm_triagem, triagem_chain, prompt_rag, document_chain).
Testar Triagem: Execute a célula que demonstra o uso da função triagem com mensagens de teste.
Testar RAG: Execute a célula que demonstra o uso da função perguntar_politica_RAG com perguntas de teste. Certifique-se de que o retriever foi criado com sucesso na etapa 5.
Estrutura do Código
Instalação de Dependências: Célula com !pip install.
Configuração da API Key: Célula para carregar a chave de API dos segredos do Colab.
Inicialização do LLM para Triagem: Célula que inicializa o modelo Gemini para a função de triagem.
Prompt de Triagem: Célula que define o prompt do sistema para a triagem.
Modelo Pydantic para Saída: Célula que define a estrutura de saída JSON esperada.
Inicialização do LLM para RAG: Célula que inicializa o modelo Gemini para as respostas RAG.
Função de Triagem: Célula que implementa a lógica da função de triagem usando a cadeia estruturada.
Testes de Triagem: Células com exemplos de mensagens para testar a triagem.
Carregamento de Documentos: Célula para carregar arquivos PDF.
Divisão de Documentos: Célula para dividir os documentos em chunks.
Inicialização de Embeddings: Célula para configurar o modelo de embeddings.
Criação do Vector Store e Retriever: Célula para criar o banco de dados vetorial FAISS e o retriever.
Prompt e Cadeia RAG: Célula para definir o prompt e criar a cadeia de documentos para o RAG.
Funções Auxiliares RAG: Células com funções para limpar texto e formatar citações.
Função Principal RAG: Célula que implementa a função perguntar_politica_RAG.
Testes RAG: Células com exemplos de perguntas para testar o sistema RAG.
