# 🎓 Sistema de Gerenciamento de Monografias - UFVJM

Este projeto tem como objetivo implementar um sistema completo para gerenciar o ciclo de vida das monografias do Curso de Sistemas de Informação da **UFVJM** – desde o cadastro do aluno até o resultado final da defesa.

---

## 📌 Objetivos

- Gerenciar monografias, bancas, orientadores e alunos
- Controlar o fluxo completo da monografia: submissão, avaliação, defesa e aprovação
- Fornecer interface administrativa com controle de permissões
- Disponibilizar API REST para integração e consulta pública de dados

---

## 🧰 Tecnologias Utilizadas

- **Backend:** [Django](https://www.djangoproject.com/) + [Django REST Framework](https://www.django-rest-framework.org/)
- **Frontend:** JavaScript + Integração via API
- **Banco de Dados:** PostgreSQL
- **Autenticação:** [django-allauth](https://django-allauth.readthedocs.io/)
- **Gráficos:** [Chart.js](https://www.chartjs.org/) ou [Plotly](https://plotly.com/)
- **PDFs:** Geração automática de ata de defesa

---

## ✅ Funcionalidades

### 🔐 Autenticação e Controle de Acesso

- Login via `django-allauth`
- Controle de acesso baseado em permissões (Administrador, Professor, Aluno)
- Políticas de senha e criptografia
- Registro de auditoria (ações dos usuários)
- Dashboard personalizado por tipo de usuário

### 📝 CRUD de Monografias

- Upload de arquivos (PDFs e documentos complementares)
- Campos obrigatórios:
  - Título
  - Autor
  - Orientador e Coorientador
  - Resumo / Abstract
  - Palavras-chave
  - Data da defesa
- Modelos principais:
  - **Aluno** (nome, matrícula, e-mail)
  - **Orientador/Coorientador** (nome, e-mail, titulação, área de pesquisa)
  - **Monografia** (título, resumo, status, arquivos, data)
  - **Banca** (avaliadores, local/data da defesa, nota final)
- Validação de dados obrigatórios

### 🔍 Leitura e Busca

- Filtro por título, orientador, palavra-chave, data, etc.
- Visualização completa da monografia
- Paginação e ordenação dos resultados

### ✏️ Atualização

- Edição completa dos dados da monografia
- Substituição de arquivos
- Controle de histórico de revisões

### 🗑️ Exclusão

- Exclusão com confirmação
- Apenas usuários autorizados podem excluir dados

---

## 📡 API REST (Django REST Framework)

### Endpoints Públicos (Somente Leitura)

- Lista de monografias aprovadas
- Lista de professores orientadores

### Endpoints Restritos (CRUD Autenticado)

- Criar / Editar / Excluir monografias
- Agendar defesas e registrar notas

### Respostas da API

- Formato: JSON
- Paginação e ordenação configuradas

---

## 📈 Funcionalidades Extras

- Geração automática de ata de defesa (PDF)
- Dashboard com gráficos (monografias por ano, área de pesquisa, status, etc.)
- Histórico de alterações em monografias (quem alterou e quando)
- Integração com frontend via JavaScript (ex: React ou Vanilla)

---

## 🏁 Como Rodar o Projeto

### Pré-requisitos

- Python 3.10+
- PostgreSQL
- Node.js (para frontend)
- Docker (opcional)

### Passos para rodar localmente

```bash
# Clone o repositório
git clone (https://github.com/KiraYagamiDark/TPSistemasDistribuidos.git
cd seu-repo

# Crie um ambiente virtual
python -m venv venv
source venv/bin/activate  # ou venv\Scripts\activate no Windows

# Instale as dependências
pip install -r requirements.txt

# Configure o banco de dados (PostgreSQL)
# Edite o arquivo settings.py com suas credenciais

# Aplique as migrações
python manage.py migrate

# Crie um superusuário
python manage.py createsuperuser

# Rode o servidor
python manage.py runserver
