# Login do Administrador

Área restrita para o administrador do restaurante editar os itens do cardápio.

## Campos

| Campo | Tipo | Obrigatório |
|---|---|---|
| E-mail | texto (e-mail) | Sim |
| Senha | texto (senha) | Sim |

## Regras

- O e-mail deve ter um formato válido (`nome@dominio.com`).
- A senha deve ter no mínimo 8 caracteres, com pelo menos uma letra maiscula e um caractere especial
- Após 3 tentativas incorretas, exibir mensagem de bloqueio temporário.
- Em caso de sucesso, redirecionar para a área de edição do cardápio.

## Histórico

---

*Projeto fictício — GCS 2026/1. Sem backend real.*
