# Desafio Criativo: Planejando Automações com N8N Usando Apenas Bons Prompts

Desafio da DIO em que se constrói, passo a passo, um prompt claro e estruturado capaz de orientar uma IA a planear uma automação em N8N.

## Objetivo

Automatizar o registo de faturas de fornecedores recebidas por e-mail, eliminando a digitação manual e sinalizando duplicados e dados em falta.

## Como o prompt foi construído

1. **Passo 1: Automação definida.** Processo, responsáveis e resultado esperado.
2. **Passo 2: Contexto e regras.** Ferramentas, fluxo em sequência e validações.
3. **Passo 3: Prompt final.** União de todas as peças num único comando.

## Prompt final

````text
Atue como um especialista em N8N.

Crie uma automação para registar automaticamente faturas de fornecedores recebidas por e-mail.

Público:
Departamento de contabilidade e administrativo, com a contabilista certificada como responsável pela validação dos casos sinalizados.

Ferramentas envolvidas:
Gmail, N8N, nó de extração de dados de PDF (OCR ou IA), Google Sheets e Google Drive.

Fluxo:
1. Detetar um novo e-mail com anexo PDF numa caixa de correio ou etiqueta de faturas (Gmail).
2. Extrair do PDF os campos: fornecedor, NIF, número da fatura, data, valor total e IVA.
3. Validar os dados: campos obrigatórios preenchidos, NIF com 9 dígitos e valor numérico.
4. Verificar se a fatura já existe na folha (mesmo NIF + mesmo número).
5. Se for válida e nova, registar uma linha no Google Sheets.
6. Guardar o PDF no Google Drive, numa pasta por ano e mês (por exemplo, 2026/10).
7. No fim do dia, enviar um resumo à equipa com o total de faturas registadas e os casos pendentes.

Regras:
- Ignorar e-mails sem anexo PDF.
- Se faltar algum campo obrigatório ou o NIF for inválido, não registar. Marcar como "Revisão manual" e avisar a contabilista.
- Se a fatura for duplicada (mesmo NIF + mesmo número), não registar de novo e sinalizar no resumo diário.
- Não apagar nem alterar linhas existentes na folha, apenas acrescentar.
- Registar na folha o estado de cada fatura: "Registada", "Duplicada" ou "Revisão manual".

Explique quais nós do N8N devem ser utilizados e a lógica de funcionamento do workflow.
````

## Ficheiros

- `prompt-final-n8n.md`: o prompt final, pronto a usar.
- `README.md`: esta descrição do desafio.

## Boas práticas aplicadas

- **Intenção clara:** processo concreto e resultado definido.
- **Contexto:** público, ferramentas e fluxo em ordem.
- **Instruções específicas:** validações, exceções e estados de cada fatura.
