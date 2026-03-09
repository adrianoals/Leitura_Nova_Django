# Leitura Nova — Water & Gas Meter Reading Management

**Web application built for Leitura Nova**

🇧🇷 [Leia em Português](README.pt-br.md)

---

Leitura Nova is a web application developed for the company **Leitura Nova** to automate and streamline water and gas meter reading management across residential condominiums. Residents access the system online, select their unit, and submit photos of their meters. The company then uses the platform to monitor and control monthly consumption.

## Tech Stack

- **Python** / **Django**
- **PostgreSQL** (Supabase)
- **Docker** / **Docker Compose**
- **Nginx** + **Gunicorn**
- **AWS EC2**
- **HTML / CSS / Bootstrap / JavaScript**

## How it Works

1. Residents receive a link to the system
2. They select their condominium and unit
3. They upload a photo of the water or gas meter
4. Leitura Nova monitors and manages monthly consumption data

## Features

- Multi-condominium support (each condominium is a separate Django app)
- Photo upload for meter readings with Supabase storage
- Monthly consumption tracking and management
- Docker containerization for consistent deployments
- Production-ready setup with Nginx + Gunicorn
- AWS EC2 hosting with Traefik reverse proxy and SSL

## Project Structure

```
Leitura_Nova_Django/
├── setup/              # Django project settings (urls, wsgi, settings)
├── alvorada/           # Condominium: Alvorada
├── imperial/           # Condominium: Imperial
├── tres_coelho/        # Condominium: Três Coelhos
├── templates/          # HTML templates for each condominium
├── static/             # Static files (CSS, JS, images)
├── docs/               # Documentation and changelogs
├── Dockerfile
├── docker-compose.yml
├── entrypoint.sh
├── requirements.txt
└── manage.py
```

## Getting Started

### Option 1: Docker

```bash
docker-compose up --build
```

### Option 2: Local Development

```bash
# Clone the repository
git clone https://github.com/your-username/Leitura_Nova_Django.git
cd Leitura_Nova_Django

# Create and activate virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env
# Edit .env with your credentials

# Run migrations
python manage.py migrate

# Start the development server
python manage.py runserver
```

Access the application at `http://localhost:8000`.

## Deployment

The application is deployed on **AWS EC2** with the following stack:

- **Traefik** as reverse proxy with automatic SSL (Let's Encrypt)
- **Gunicorn** as the WSGI application server (3 workers, 120s timeout)
- **Docker Compose** for container orchestration
- **Supabase** for PostgreSQL database and file storage

## Environment Variables

Create a `.env` file in the project root. See `.env.example` for reference:

| Variable | Description |
|---|---|
| `SECRET_KEY` | Django secret key |
| `POSTGRES_DB` | PostgreSQL database name |
| `POSTGRES_USER` | PostgreSQL username |
| `POSTGRES_PASSWORD` | PostgreSQL password |
| `DB_HOST` | Database host |
| `DB_PORT` | Database port (default: 5432) |
| `SUPABASE_URL` | Supabase project URL |
| `SUPABASE_KEY` | Supabase anonymous/public key |

## License

This project is licensed under the [MIT License](LICENSE).
