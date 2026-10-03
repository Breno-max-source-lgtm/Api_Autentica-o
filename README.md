# API de autenticação

API REST construída com FastAPI, SQLAlchemy e SQLite. Oferece cadastro de usuários, login com token JWT e consulta do usuário autenticado.

## Requisitos

- Python 3.10 ou superior
- `pip`

## Configuração no Windows PowerShell

Na pasta `api_autenticacao`, crie e ative um ambiente virtual e instale as dependências:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Configure uma chave JWT segura para esta sessão do PowerShell e inicie a API:

```powershell
$env:JWT_SECRET_KEY = python -c "import secrets; print(secrets.token_urlsafe(48))"
uvicorn main:app --reload
```

Para produção, configure `JWT_SECRET_KEY` no ambiente do servidor e mantenha o mesmo valor entre reinicializações. Não publique essa chave no repositório.

## Endpoints

- `POST /register`: cadastra um usuário.
- `POST /login`: verifica as credenciais e retorna um token de acesso.
- `GET /users/me`: retorna os dados do usuário autenticado.
- `GET /docs`: abre a documentação interativa do FastAPI.

O banco SQLite `database.db` é criado localmente na primeira execução e fica fora do controle de versão.
