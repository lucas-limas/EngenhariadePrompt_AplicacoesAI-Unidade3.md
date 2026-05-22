# Projeto Módulo 3 – Low Code/No Code/Vibecode

## 📌 Desafio Escolhido

A ideia do projeto surgiu de um problema real que a gente viu acontecer: corretores de plano de saúde ainda usam planilha de Excel pra fazer cotação. O corretor abre a planilha, digita as idades dos clientes, vai abrindo tabela por tabela de cada operadora, e no final tenta montar uma apresentação decente no PowerPoint. Dá muito trabalho, demora bastante, e o resultado ainda é feio.

Decidimos fazer um sistema de cotação de planos de saúde para a corretora **Saúde Prime**, de Brasília. O corretor informa as idades e quantidades de pessoas, e o sistema compara automaticamente os preços de 9 operadoras. Com um clique, gera uma apresentação em PDF formatada e pronta para o cliente — sem internet, sem servidor, sem mensalidade.

Um detalhe que tornou o desafio mais interessante: alguns clientes têm CNPJ mas querem contratar como pessoa física. O sistema precisava comparar planos de modalidades diferentes (PME, Adesão, PF) na mesma tela, o que não é trivial porque cada modalidade tem regras e faixas de preço diferentes.

---

## 🖥️ Protótipo

- **Sistema hospedado:** [lucas-limas.github.io/saude-prime-sistema-comercial](https://lucas-limas.github.io/saude-prime-sistema-comercial/)
- **Relatório completo:** [relatorio.pdf](docs/relatorio.pdf)

O sistema é dividido em três arquivos que funcionam juntos:

1. **`cotador-planos-saude.html`** — tela principal onde o corretor seleciona faixas etárias, quantidade de vidas e modalidade. Exibe preços de 9 operadoras com abas de rede credenciada e carências.
2. **`dados.js`** — base de dados central com todos os preços, planos e regras. Única fonte de verdade do sistema.
3. **`apresentacao-executiva.html`** — recebe os dados do cotador e gera um PDF com capa institucional, tabela de preços, carências e chamada para ação com validade da proposta.

> Coloque os arquivos de imagem ou PDF na pasta `/docs`.

---

## ⚙️ Plataforma Utilizada

**Plataforma:** Claude Code (Anthropic) — abordagem **Vibecode** /
              Copilot - abordagem **no code**            

A escolha foi motivada por três razões práticas:

- O sistema precisava funcionar **100% offline** — ferramentas como Bubble ou Make dependem de servidores próprios. Com vibecode, o resultado é código HTML/JS puro que roda em qualquer navegador.
- As **regras de negócio do mercado de saúde** são específicas demais para blocos visuais de no-code tradicional (diferença entre ARC 400 e ARC 500, modelo RC1/RC2/RC3 da Evo, critérios de IMC da Plenum etc.).
- A **velocidade de iteração** foi maior: descrevíamos o que queríamos em português e o modelo gerava o código. As correções chegavam em minutos, não em horas.

---

## ✅ Vantagens Identificadas

1. **Velocidade de desenvolvimento** — funcionalidades que levariam dias foram feitas em horas. Com especificação precisa, o código saía certo na primeira tentativa.
2. **Zero infraestrutura** — nenhuma mensalidade, nenhum servidor, nenhum banco de dados pago. O sistema inteiro são três arquivos HTML.
3. **Arquitetura emergente** — a separação entre `dados.js` e as telas surgiu naturalmente durante o processo. Aprendemos um padrão de arquitetura real sem ter estudado formalmente.
4. **Ciclo de feedback curtíssimo** — ver no navegador → identificar o problema → descrever em texto → receber a correção. Sem compilar, sem fazer deploy.
5. **Código aberto e portável** — diferente de um sistema feito em Bubble, que fica preso na plataforma, o resultado aqui é código que qualquer desenvolvedor consegue entender e manter.

---

## ⚠️ Limitações Encontradas

1. **Perda de contexto entre sessões** — as conversas foram longas e em vários dias. A cada nova sessão, era necessário recontextualizar a arquitetura e as decisões tomadas.
2. **Ausência de testes automatizados** — nenhum teste unitário foi escrito. Os bugs só apareciam durante testes manuais com dados reais. Em produção, isso seria um risco.
3. **Manutenção requer conhecimento técnico** — não tem interface de administração amigável. Atualizar preços exige editar o `dados.js` diretamente.
4. **PDF via navegador é inconsistente** — cada sistema operacional e versão de Chrome se comporta de forma diferente na impressão. Foram várias iterações ajustando o CSS de `@media print`.
5. **Dependência da qualidade da especificação** — descrições vagas geravam código errado. Vibecode não substitui saber o que se quer.

---

## 📚 Reflexão Crítica

**Sobre a perda de contexto:** criamos um arquivo `MEMORY.md` com registro das decisões técnicas, arquitetura e estado atual do projeto. No início de cada nova sessão, esse contexto era colado. Foi manual, mas funcionou.

**Sobre a falta de testes:** adotamos uma política de testar na prática antes de commitar. Cada funcionalidade nova era exercida com dados reais — idades reais, operadoras reais, cenários com e sem ARC — antes de ir pro Git.

**Sobre manutenção:** separamos todo o dado de preços no `dados.js` com estrutura documentada. A ideia é que uma atualização futura de preço possa ser feita por alguém com conhecimento básico de JavaScript.

**Sobre o PDF:** as inconsistências se concentravam em `@page margins` e `break-inside: avoid`. A solução foi testar especificamente no Chrome e documentar isso para quem for usar.

> A lição mais importante: vibecode não elimina a necessidade de entender o problema. O modelo é eficiente em traduzir intenções bem articuladas em código — mas se você não sabe o que quer, o código não vai te salvar.

---

## 👥 Colaboração

O trabalho foi dividido em quatro frentes:

| Integrante | Responsabilidade |
|---|---|
| João Pedro de Sousa Corrêa Teixeira | Requisitos — entrevistas com corretores reais para mapear o fluxo atual |
| Breno Amorim da Silva | Dados — coleta e validação das tabelas de preços e carências das operadoras |
| Bianca Moura Sena Araújo | Desenvolvimento — sessões de vibecode, revisão de código e gestão do Git |
| Cauã Spinola de Oliveira | Desenvolvimento — testes funcionais e integração entre os módulos |
| Gabriella Barbosa Neves | Design/UX — paleta de cores, hierarquia visual e testes com o corretor em campo |
| Lucas Lima Nascimento | Desenvolvimento — arquitetura do sistema e gerador de apresentação PDF |

As sessões de desenvolvimento eram feitas em dupla — alguém do lado técnico e alguém que conhecia o domínio do negócio. Isso ajudou a pegar erros de lógica que o código gerava correto tecnicamente, mas que não faziam sentido para quem é corretor de saúde.

---

## 📝 Registro da Aula

**Data:** 22/05/2026  
**Atividade:** Discussão crítica + mini-projeto de aplicação  
**Local:** Laboratório de informática / Quadro branco  
**Professor(a):** Kadidja Valéria  

---

## 🚀 Próximos Passos

**Melhorias imediatas:**
- Painel de admin simples: formulário HTML onde o corretor atualiza preços sem editar o `dados.js` na mão
- Botão de compartilhar pelo WhatsApp: integração com a API do WhatsApp Web para enviar a apresentação diretamente
- Histórico de cotações: salvar no `localStorage` do navegador as cotações anteriores

**Evoluções para o Projeto Final:**
- Migrar o `dados.js` para um banco de dados em nuvem (Supabase, plano gratuito) com API simples — atualizações de preço feitas de qualquer dispositivo
- Autenticação por corretor, com histórico individual e cálculo de comissões
- Geração de apresentação via API do Claude com texto personalizado por cliente, tornando cada proposta genuinamente única
