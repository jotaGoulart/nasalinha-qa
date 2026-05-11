# NaSalinha QA — Auditoria de Qualidade

Documentação da auditoria de qualidade realizada no projeto NaSalinha, 
um sistema de check-in gamificado onde membros fazem upload de fotos, 
acumulam pontos e sobem no ranking.

---

## Sobre o projeto auditado

O NaSalinha é uma aplicação web onde membros realizam check-ins diários 
com fotos como prova de presença. Administradores aprovam os check-ins 
e os pontos são refletidos em um ranking geral por temporada.

**Stack do projeto:**
- Frontend: React 18 + TailwindCSS
- Backend: Node.js + Express + Prisma ORM
- Banco de dados: PostgreSQL
- Serviços externos: Cloudinary (fotos) e Ethereal Email (e-mails de teste)
- Infraestrutura: Docker + Docker Compose

---

## Ferramentas utilizadas nos testes

- **Insomnia** - testes de API e validação de endpoints
- **Docker Desktop** - ambiente local do projeto
- **GitHub Issues** - registro de bug reports
- **GitHub Projects** - kanban e acompanhamento dos casos de teste
- **Ethereal Email** - captura dos e-mails enviados pelo sistema

---

## Estrutura do repositório

- `docs/relatorio-final.md` - relatório final com métricas e resultados
- `colecoes-api/nasalinha-insomnia.yaml` - coleção exportada do Insomnia
- Casos de teste e bug reports estão documentados no GitHub Issues e Projects

---

## O que foi testado

Foram testadas as 3 áreas core do sistema e, como diferencial, 
o CRUD completo de temporadas:

- Autenticação JWT - cadastro, login, controle de acesso e segurança
- Check-in por foto - upload, fluxo de status e restrições
- Pontos e ranking - atribuição, consistência e ordenação
- Temporadas - criação, edição, listagem e remoção

Os testes foram divididos em funcionais (interface), de API (Insomnia) 
e de regressão, além de um caso ad-hoc identificado durante a execução.

---

## Resultados

26 casos de teste executados com 9 bugs encontrados.
Consulte o [Relatório Final](docs/relatorio-final.md) para detalhes completos.