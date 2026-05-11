# Relatório Final de Testes - NaSalinha

**Data de execução:** abril-maio de 2026
**Responsável:** Juliano Vieira Goulart
**Projeto auditado:** NaSalinha QA

---

## Métricas de Execução

| Métrica | Quantidade |
|---|---|
| Casos de teste planejados | 26 |
| Casos de teste executados | 26 |
| Aprovados (Pass) | 18 |
| Reprovados (Fail) | 7 |
| Inconclusivos | 1 |

---

## Distribuição de Severidade dos Bugs

| Severidade | Quantidade | Bugs |
|---|---|---|
| Crítico | 6 | BUG-001, BUG-002, BUG-004, BUG-005, BUG-006, BUG-008 |
| Maior | 3 | BUG-003, BUG-007, BUG-009 |
| Menor | 0 | — |

---

## Resultado por Área

| Área | Total | Pass | Fail | Inconclusivo |
|---|---|---|---|---|
| Autenticação JWT | 8 | 6 | 2 | 0 |
| Check-in por Foto | 8 | 3 | 4 | 1 |
| Pontos e Ranking | 4 | 3 | 1 | 0 |
| Temporadas | 6 | 5 | 1 | 0 |

---

## Bugs Encontrados

| ID | Área | Severidade | Descrição |
|---|---|---|---|
| BUG-001 | Configuração | Crítico | EMAIL_HOST inválido no .env.example |
| BUG-002 | JWT | Crítico | E-mail de boas-vindas sem código de verificação |
| BUG-003 | JWT | Maior | Mensagem de erro incorreta ao logar sem verificação |
| BUG-004 | JWT | Crítico | Rota /api/seasons acessível por usuários MEMBER |
| BUG-005 | Check-in | Crítico | Sistema permite múltiplos check-ins no mesmo dia |
| BUG-006 | Check-in | Crítico | Check-ins criados com status APROVADO automaticamente |
| BUG-007 | Check-in | Maior | Usuário visualiza check-ins de outros usuários |
| BUG-008 | Pontos | Crítico | Pontos não subtraídos ao deletar check-in |
| BUG-009 | Check-in | Maior | Sistema permite envio da mesma foto repetidas vezes |

---

## Estratégia de Regressão

Para ilustrar a estratégia de regressão, tomei como base a correção do BUG-004,
onde a rota /api/seasons estava acessível por usuários com perfil MEMBER.

Após a correção, repetiria os seguintes testes para garantir que nada foi quebrado:

1. CT-06 — Admin ainda acessa /api/seasons normalmente (esperado: 200)
2. CT-05 — MEMBER agora recebe 403 ao tentar acessar a mesma rota
3. CT-04 — Login do Admin continua funcionando normalmente
4. Testar outras rotas restritas a ADMIN: DELETE /seasons e POST /seasons
5. Confirmar que rotas públicas não foram impactadas pela correção

A ideia é garantir que ao corrigir o controle de acesso em um endpoint,
o fluxo de autenticação e as demais rotas do sistema continuem funcionando.

---

## Conclusão

O sistema apresenta problemas sérios que precisam ser resolvidos antes
de qualquer uso em produção. As falhas mais graves estão no controle de
acesso, no fluxo de moderação de check-ins e na consistência do sistema
de pontos, áreas que afetam diretamente a segurança e a confiabilidade
da aplicação.

No geral, as funcionalidades básicas de autenticação e navegação funcionam,
mas o núcleo do produto, que envolve check-ins, pontos e ranking, apresenta
comportamentos incorretos que comprometem a experiência do usuário e a
integridade dos dados.