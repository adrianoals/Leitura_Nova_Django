# Leitura Nova — Gestão de Leituras de Água e Gás

**Aplicação web desenvolvida para a empresa Leitura Nova**

🇺🇸 [Read in English](README.md)

---

Leitura Nova é uma aplicação web desenvolvida para a empresa **Leitura Nova** para automatizar e otimizar o gerenciamento de leituras de hidrômetros de água e medidores de gás em condomínios residenciais. Os moradores acessam o sistema online, selecionam sua unidade e enviam fotos dos medidores. A empresa utiliza a plataforma para monitorar e controlar o consumo mensal.

## Tecnologias

- **Python** / **Django**
- **PostgreSQL** (Supabase)
- **Docker** / **Docker Compose**
- **Nginx** + **Gunicorn**
- **AWS EC2**
- **HTML / CSS / Bootstrap / JavaScript**

## Como Funciona

1. Os moradores recebem um link para o sistema
2. Selecionam o condomínio e a unidade
3. Enviam uma foto do medidor de água ou gás
4. A Leitura Nova monitora e gerencia os dados de consumo mensal

## Funcionalidades

- Suporte a múltiplos condomínios (cada condomínio é um app Django separado)
- Upload de fotos dos medidores com armazenamento no Supabase
- Acompanhamento e gestão do consumo mensal
- Containerização com Docker para deploys consistentes
- Configuração pronta para produção com Nginx + Gunicorn
- Hospedagem na AWS EC2 com Traefik como proxy reverso e SSL

## Estrutura do Projeto

```
Leitura_Nova_Django/
├── setup/              # Configurações do projeto Django (urls, wsgi, settings)
├── alvorada/           # Condomínio: Alvorada
├── imperial/           # Condomínio: Imperial
├── tres_coelho/        # Condomínio: Três Coelhos
├── templates/          # Templates HTML para cada condomínio
├── static/             # Arquivos estáticos (CSS, JS, imagens)
├── docs/               # Documentação e changelogs
├── Dockerfile
├── docker-compose.yml
├── entrypoint.sh
├── requirements.txt
└── manage.py
```

## Começando

### Opção 1: Docker

```bash
docker-compose up --build
```

### Opção 2: Desenvolvimento Local

```bash
# Clone o repositório
git clone https://github.com/your-username/Leitura_Nova_Django.git
cd Leitura_Nova_Django

# Crie e ative o ambiente virtual
python3 -m venv .venv
source .venv/bin/activate

# Instale as dependências
pip install -r requirements.txt

# Configure as variáveis de ambiente
cp .env.example .env
# Edite o .env com suas credenciais

# Execute as migrações
python manage.py migrate

# Inicie o servidor de desenvolvimento
python manage.py runserver
```

Acesse a aplicação em `http://localhost:8000`.

## Deploy

A aplicação é implantada na **AWS EC2** com a seguinte stack:

- **Traefik** como proxy reverso com SSL automático (Let's Encrypt)
- **Gunicorn** como servidor WSGI (3 workers, timeout de 120s)
- **Docker Compose** para orquestração de containers
- **Supabase** para banco de dados PostgreSQL e armazenamento de arquivos

## Variáveis de Ambiente

Crie um arquivo `.env` na raiz do projeto. Veja o `.env.example` como referência:

| Variável | Descrição |
|---|---|
| `SECRET_KEY` | Chave secreta do Django |
| `POSTGRES_DB` | Nome do banco de dados PostgreSQL |
| `POSTGRES_USER` | Usuário do PostgreSQL |
| `POSTGRES_PASSWORD` | Senha do PostgreSQL |
| `DB_HOST` | Host do banco de dados |
| `DB_PORT` | Porta do banco de dados (padrão: 5432) |
| `SUPABASE_URL` | URL do projeto Supabase |
| `SUPABASE_KEY` | Chave anônima/pública do Supabase |

## Licença

Este projeto é licenciado sob a [MIT License](LICENSE).
