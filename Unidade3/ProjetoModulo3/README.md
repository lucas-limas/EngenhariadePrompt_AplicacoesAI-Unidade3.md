# Cotador de Planos de Saúde — Saúde Prime

> Projeto desenvolvido para o Módulo 3 – Low Code / No Code / Vibecode  
> Curso de Engenharia de Software — 2026/1

---

## Sobre o Projeto

Sistema comercial completo para corretores de planos de saúde, desenvolvido com a abordagem **Vibecode** (desenvolvimento assistido por IA via Claude Code).

O sistema resolve um problema real do dia a dia de corretores: a cotação manual via planilhas de Excel, que é lenta, propensa a erros e gera apresentações pouco profissionais para os clientes. Com esta ferramenta, o corretor informa as idades e quantidades de vidas, compara automaticamente os preços de 9 operadoras e gera uma apresentação em PDF com um clique — sem internet, sem servidor, sem mensalidade.

---

## Demonstração

**Sistema hospedado:** [lucas-limas.github.io/saude-prime-sistema-comercial](https://lucas-limas.github.io/saude-prime-sistema-comercial/)


**Relatório completo do projeto:** [relatorio.pdf](docs/relatorio.pdf)

---

## Funcionalidades

- **Cotação simultânea** de 9 operadoras: Unity, Evo, Plenum, Amil, MedSênior, Seguros Unimed, Porto Saúde, Bradesco e Best Sênior
- **Comparação entre modalidades**: PME, Adesão e Pessoa Física na mesma tela (inclusive cotações mistas)
- **Aba de rede credenciada**: hospitais e clínicas por operadora
- **Aba de carências**: tabelas detalhadas com prazos por procedimento e código de cores (imediato / moderado / pleno)
- **Gerador de apresentação em PDF**: capa institucional, tabela de preços por faixa etária, carências, rede credenciada e chamada para ação com validade da proposta
- **Funciona 100% offline**: nenhuma dependência de servidor ou internet

---

## Estrutura do Sistema

```
cotador-planos-saude.html    # Tela principal de cotação
apresentacao-executiva.html  # Gerador de apresentação PDF
dados.js                     # Base de dados central (preços, planos, operadoras)
```

O `dados.js` é a única fonte de verdade para todos os dados de preços e regras das operadoras. Qualquer atualização de tabela é feita exclusivamente neste arquivo, sem precisar tocar nas telas.

---

## Como Usar

1. Faça o download ou clone este repositório
2. Abra `cotador-planos-saude.html` em qualquer navegador moderno (Chrome recomendado)
3. Selecione as faixas etárias, quantidade de vidas e modalidade de contratação
4. Compare os preços e detalhes das operadoras nas abas disponíveis
5. Clique em **"Gerar Apresentação"** para abrir o gerador de PDF
6. No gerador, selecione as opções desejadas e use `Ctrl+P` (ou `Cmd+P`) para salvar como PDF

> Nenhuma instalação necessária. Nenhuma conexão com internet.

---

## Stack Tecnológica

| Tecnologia | Uso |
|---|---|
| HTML5 / CSS3 | Interface e layout das telas |
| JavaScript (Vanilla) | Lógica de cotação, filtros e geração de apresentação |
| CSS `@media print` | Geração de PDF via impressão do navegador |
| Git + GitHub | Versionamento e portfólio |
| **Claude Code (Anthropic)** | Desenvolvimento assistido por IA (Vibecode) |

---

## Abordagem de Desenvolvimento: Vibecode

Este projeto foi desenvolvido integralmente com a abordagem **Vibecode** — o desenvolvedor descreve em linguagem natural o comportamento desejado, e o modelo de IA (Claude Code) gera, refatora e corrige o código em tempo real.

### O que funcionou bem
- Velocidade de desenvolvimento: funcionalidades que levariam dias foram feitas em horas
- A arquitetura (separação do `dados.js`) emergiu naturalmente durante as sessões
- Ciclo de feedback curtíssimo: testar no navegador → descrever o problema → receber a correção

### O que aprendemos na prática
- Vibecode não substitui entender o problema — especificações vagas geram código errado
- A falta de testes automatizados exigiu uma disciplina rígida de testes manuais antes de cada commit
- Sessões longas demandam gestão ativa de contexto para o modelo não perder coerência

---

## Contexto Acadêmico

**Disciplina:** Engenharia de Prompt e Aplicações de IA  
**Módulo:** 3 — Low Code / No Code / Vibecode  
**Professor(a):** Kadidja Valéria  
**Instituição:** [Nome da Instituição]  
**Semestre:** 2026/1

---

## Autor

**Lucas Limas**  
Engenharia de Software — 2º Semestre  
[github.com/lucas-limas](https://github.com/lucas-limas)
