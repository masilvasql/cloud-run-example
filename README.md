# Passo 1: Autenticação
gcloud auth login

# Passo 2: Definir Projeto e Região
gcloud config set project pos-full-cycle
gcloud config set run/region us-central1

# Passo 3: Ir para o Diretório com o Dockerfile
cd /caminho/para/meu-projeto

# Passo 4: Criar a Imagem e Enviar para o Container Registry
gcloud builds submit --tag gcr.io/pos-full-cycle/example-cloud-run .

# Passo 5: Publicar no Cloud Run
gcloud run deploy NOME-DO-SERVICO-QUE-QUER-GERAR --image gcr.io/pos-full-cycle/example-cloud-run --platform managed

# Passo 6: Tornar o Serviço Público (opcional)
gcloud run services add-iam-policy-binding NOME-DO-SERVICO-QUE-QUER-GERAR --member="allUsers" --role="roles/run.invoker"
