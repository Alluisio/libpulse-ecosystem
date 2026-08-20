# 🎮 LibPulse Ecosystem

> **Repositório central (Umbrella Repository) do ecossistema LibPulse.**  
> Monitoramento contínuo, inteligência e notificações para bibliotecas Steam e Steam Family.

Este repositório consolida todos os serviços, aplicações e infraestrutura do ecossistema **LibPulse** através de **Git Submodules**.

---

## 🏛️ Topologia e Arquitetura

O ecossistema é dividido em três aplicações principais:

```text
libpulse-ecosystem/
├── libpulse-backend/      # [Submódulo] API RESTful NestJS + TypeORM + PostgreSQL
├── libpulse-ui/           # [Submódulo] Painel Web React 19 + Vite + PrimeReact
├── libpulse-mobile/       # [Submódulo] Aplicativo Móvel Expo SDK 57 + React Native
└── docker-compose.yml     # Orquestração local do banco de dados e serviços
```

### Componentes

1. 🎮 **[libpulse-backend](https://github.com/Alluisio/libpulse-backend.git)**: Serviço central em NestJS responsável pela sincronização com a Steam Web API / Store API, detecção de novos jogos na família, rastreamento de descontos em DLCs, motor de recomendações e disparo de digests por e-mail e push.
2. 🌐 **[libpulse-ui](https://github.com/Alluisio/libpulse-ui.git)**: Painel web (SPA) construído em React 19, Vite, TypeScript e PrimeReact para visualização de estatísticas, catálogo e configurações em desktop.
3. 📱 **[libpulse-mobile](https://github.com/Alluisio/libpulse-mobile.git)**: Aplicativo para iOS e Android em Expo e React Native com notificações push nativas em tempo real e dashboard portátil.

---

## 🚀 Como Clonar e Inicializar o Repositório

### 1. Clonar com todos os submódulos de uma vez
```bash
git clone --recurse-submodules https://github.com/Alluisio/libpulse-ecosystem.git
cd libpulse-ecosystem
```

### 2. Se já clonou sem a flag `--recurse-submodules`:
```bash
git submodule update --init --recursive
```

---

## 🔄 Atualizando Submódulos

Para sincronizar todos os submódulos com as versões mais recentes das branches remotas:

```bash
git submodule update --remote --merge
```

---

## 🐳 Infraestrutura com Docker Compose

Para subir o banco de dados PostgreSQL com as credenciais padrão do backend:

```bash
# Iniciar o PostgreSQL em background
docker compose up -d postgres

# Verificar logs do container
docker compose logs -f postgres

# Parar os containers
docker compose down
```

### Credenciais Padrão do Banco de Dados
* **Host:** `localhost`
* **Porta:** `5432`
* **Usuário:** `postgres`
* **Senha:** `postgres`
* **Database:** `libpulse`

---

## 🛠️ Tecnologias Principais

* **Backend:** Node.js, NestJS v11, TypeORM, PostgreSQL 16, Nodemailer, Swagger.
* **Frontend Web:** React 19, Vite, TypeScript, PrimeReact, PrimeFlex, TanStack Query v5.
* **Mobile:** Expo SDK 57, React Native, React Navigation, TanStack Query v5, Expo Notifications.
* **DevOps:** Docker, Docker Compose, Git Submodules.
