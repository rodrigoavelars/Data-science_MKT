# 🍕 Pizza à Bessa x Valentina: o que faz um Reel render mais visualizações?

> **Análise de 58 Reels do Instagram que mostra quais tipos de conteúdo atraem mais visualizações e transforma isso em uma campanha testável para a Pizza à Bessa.**

**Disciplina:** Ciência de Dados aplicada ao Marketing Digital, CEUB | **Profa.:** Kadidja Valéria Reginaldo de Oliveira

Projeto feito com a metodologia **CRISP-DM**, usando apenas **dados públicos** (Instagram, Biblioteca de Anúncios do Meta, Google Trends e Google Maps). Não tivemos acesso a dados internos da pizzaria.

---

## Resumo em 6 linhas
1. O Reel típico da Bessa tem **~30x mais visualizações** que o da Valentina (70,7 mil contra 2,3 mil).
2. Mesmo assim, a Valentina **anuncia mais**: 22 anúncios (um com 656 dias no ar) contra 4 da Bessa, e posta 4 vezes por mês contra 2.
3. Na Bessa, Reels de **novo sabor** são o fator que mais pesa: o Reel típico tem **254 mil** visualizações, contra **57,5 mil** dos demais.
4. O modelo confirma: novo sabor traz cerca de **7x mais** visualizações. Aparecer o Paulo Bessa e mostrar o ambiente também ajudam (~2x cada), mas são só **indícios**.
5. Proposta: campanha **"Sabor novo do mês"**, com Paulo Bessa, medida por **custo por contato**.
6. **Impacto social:** acesso à informação com acessibilidade (texto na tela, instrução de como reservar e resposta ao público), medido por compreensão e conclusão de reservas, e não só por visualizações. A mudança é **esperada**: ainda não foi medida.

---

## 1. Compreensão do Negócio
* **Problema:** a Bessa tem Reels que viralizam (mais de 400 mil visualizações), mas não aproveita isso: ~2 posts por mês, 4 anúncios com mensagens repetidas há mais de 90 dias, stories desatualizados e marca dividida em vários perfis. Ela não sabe quais conteúdos mais atraem o público.
* **Objetivo:** descobrir quais características de um Reel estão ligadas a mais visualizações e usá-las para planejar conteúdo e anúncios.
* **Critérios de sucesso:** (1) achar fatores de conteúdo ligados às visualizações; (2) modelo que erre menos que um "chute na média"; (3) campanha testável, com indicador e cuidado com dados.
* **Limite:** sem vendas, gasto em anúncios nem seguidores. **Não calculamos ROI.**

## 2. Compreensão dos Dados
| Fonte | O que coletamos |
|---|---|
| Instagram | Visualizações de 58 Reels (35 da Bessa e 23 da Valentina), lidas de prints |
| Biblioteca de Anúncios (Meta) | Bessa: 4 anúncios (91 a 119 dias). Valentina: 22 (o mais antigo com 656 dias) |
| Google Trends (DF, 2026) | "pizza" média 81; "pizza bessa" 14; "valentina pizzaria" 9 |
| Google Maps | Bessa 4,4 (5.561 avaliações); Valentina 4,6 e 4,5 (2.792 e 2.531) |
| Estudo de caso do grupo | Posts por mês, stories, verificação, aplicativo, serviço e tempo de espera |

**Período:** consultas do grupo em nov/2026 (Google Trends: DF, jan a nov/2026).
**Problemas nos dados:** amostra pequena; classificação feita à mão e revisada pelo grupo; sem datas dos posts e sem seguidores.

## 3. Preparação dos Dados
Mantivemos só Reels com visualizações e transformamos cada característica em sim/não: é da Bessa? é novo sabor? aparece o Paulo Bessa ou influenciador? mostra o ambiente? Aplicamos um ajuste técnico às visualizações (escala logarítmica) para os vídeos gigantes não distorcerem o cálculo.

## 4. Modelagem
Comparamos 3 métodos, testando sempre em Reels que o modelo não viu (validação repetida 100 vezes):

| Método | Erro típico | R² |
|---|---|---|
| Chutar a média (régua) | 5,5x | -0,20 |
| **Regressão linear (modelo final)** | **2,8x** | **0,44** |
| Random Forest | 3,1x | 0,35 |
| Regressão linear com 9 perguntas | 3,2x | 0,27 |
| Só Bessa (35 Reels), regressão linear | 3,0x | -0,17 |

*Transparência:* escolhemos as 4 perguntas depois de ver que 9 funcionavam pior. É um bom indício, não uma garantia.

## 5. Avaliação
| Característica | Efeito | Variação possível | Conclusão |
|---|---|---|---|
| **Reel de novo sabor** | ~6,9x | 3,2x a 13,5x | **Confirmado** |
| Ser o perfil da Bessa | ~9,9x | 5,1x a 18,6x | Confirmado, mas mistura conteúdo com tamanho da audiência |
| Paulo Bessa ou influenciador | ~2,2x | 0,9x a 4,9x | Indício |
| Mostrar o ambiente | ~1,9x | 0,6x a 5,6x | Indício |

**Critérios de sucesso:** fatores encontrados ✅ (novo sabor confirmado, 2 indícios) | modelo melhor que o chute ✅ | campanha testável ✅.

**O que não dá para afirmar:** que datas especiais rendem mais (a amostra não confirma); que influenciadores funcionam (resultado inconsistente); ROI (sem gasto nem vendas); que a Bessa "faz conteúdo 10x melhor" (não temos seguidores).

## 6. Implantação: campanha "Sabor novo do mês"
| Elemento | Proposta |
|---|---|
| Gatilho | Lançamento de um sabor novo por mês |
| Público | Pessoas de Brasília que interagiram com o Instagram da Bessa nos últimos 30 dias |
| Canal | Instagram e Facebook (Reel patrocinado), com botão de WhatsApp/ligar |
| Ação | Reel com Paulo Bessa provando o sabor, por 7 dias, no lugar de um anúncio parado |
| Indicador | Custo por contato (WhatsApp/ligação) e visualizações |
| Cuidado com dados (LGPD) | Só públicos de engajamento da plataforma; frequência limitada; WhatsApp só com quem iniciou a conversa; nenhum dado pessoal coletado |

**Teste A/B:** com Paulo x sem Paulo; mesmo sabor, verba e período; público dividido ao acaso; só uma variável muda; mínimo de 7 dias.
**Métricas de negócio (a pizzaria preenche):** CAC = gasto ÷ novos clientes; LTV = margem mensal × meses de relacionamento; ROI = (margem extra − investimento) ÷ investimento. Não calculadas por falta de dados.
**Próximo ciclo:** 100+ Reels por perfil, com datas e seguidores. O calendário de conteúdo de 6 meses está no notebook.

---

## Impacto social e inovação na estratégia de Marketing Digital

Versão resumida; a seção completa (inclui fontes, período e limites dos dados, e os critérios para ajustar ou interromper a estratégia) está no notebook, depois da Fase 6. Separamos sempre o **observado** (está nos nossos dados) do **esperado** (ainda precisa ser verificado).

### 1. Necessidade social e impactos escolhidos
**Necessidade social escolhida: acesso à informação, com acessibilidade.** Quem decide onde comer, comemorar ou reservar mesa em Brasília depende das redes sociais e das avaliações. Uma decisão de Marketing Digital pode reduzir esse problema (informação clara, acessível e com resposta) ou agravá-lo (informação espalhada, só em vídeo, sem retorno).

- **O que observamos (diagnóstico):** a informação da Bessa está dispersa: marca dividida em 5 ou mais perfis de Instagram, stories desatualizados, perfil sem verificação e só ~2 posts por mês (estudo de caso do grupo). No Google Trends (DF, 2026) o interesse por "pizza" é 81 e pela marca "pizza bessa" é 14: o público descobre pizzaria pela busca genérica e pelas redes, não procurando a marca pelo nome.
- **Quem enfrenta o problema:** clientes e famílias de Brasília que decidem pelas redes (qual é o sabor novo? quanto custa? como reservo para um grupo?) e pessoas que encontram barreiras para acessar o conteúdo (assistem sem som ou não usam Instagram).
- **Objetivo de Marketing Digital:** a campanha "Sabor novo do mês", com Paulo Bessa (Fase 6), para gerar mais contatos a partir do tipo de Reel que mais rende visualizações.
- **Mudança social esperada (ainda não medida):** com informação clara e acessível, resposta ágil e avaliações honestas, a pessoa decide e reserva com menos barreiras.

**Os dois impactos sociais escolhidos e por que combinam com o nosso projeto:**

| Impacto | O que observamos nos nossos dados |
|---|---|
| **1. Comunidade e relacionamento, com o dono como porta-voz** | Paulo Bessa ou influenciador no vídeo tem efeito de ~2x nas visualizações, mas só como indício (0,9x a 4,9x). O Reel "Só tenho a agradecer a vocês, Brasília" teve 56,7 mil visualizações. O salão para 500 pessoas e a área kids mostram que a Bessa é lugar de reunir grupos e famílias. Os anúncios atuais já convidam: "Ligue ou mande mensagem e tire todas as suas dúvidas" |
| **2. Prova social e avaliações** | A Bessa tem nota 4,4 em 5.561 avaliações no Google Maps. O tempo de espera aparece como ponto forte frente à Valentina, e as reclamações de atendimento aparecem nas duas marcas (estudo de caso do grupo) |

### 2. Públicos, benefícios e riscos
| Público | Como a estratégia pode afetá-lo | Benefício social | Risco ou efeito negativo | Medida para reduzir o risco |
|---|---|---|---|---|
| **Clientes e famílias de Brasília que decidem pelas redes** | Recebem o aviso do sabor novo e podem tirar dúvidas com quem responde pela pizzaria | Informação clara (sabor, valor, como reservar) e resposta mais ágil; decisão apoiada em avaliações reais | Decidir com base em avaliação incentivada ou em influenciador sem aviso de publicidade | Marcar **#publi** nas parcerias, não trocar brinde por avaliação e responder também as avaliações negativas |
| **Pessoas com barreiras de acesso ao conteúdo** (assistem sem som, têm deficiência auditiva ou não usam Instagram) | Hoje parte da informação pode estar só no vídeo ou só no Instagram | Texto na tela e instrução de como pedir ou reservar dentro do próprio Reel; telefone e WhatsApp como alternativa ao Instagram | Ficar de fora se a informação continuar só no vídeo falado ou só no Instagram | Texto na tela em todos os Reels de sabor novo, telefone e WhatsApp sempre divulgados e valor e horário também no Google Maps |
| **Equipe da pizzaria** (aparece nos vídeos) | Ganha visibilidade nos Reels com a equipe e o dono | Reconhecimento do trabalho | Exposição de imagem sem consentimento e de dados pessoais em comentários e mensagens | Autorização de uso de imagem; dúvidas individuais e dados pessoais só no WhatsApp (canal privado), nunca nos comentários |

**Efeito não previsto a acompanhar:** se a campanha trouxer mais clientes, o tempo de espera (hoje um ponto forte da Bessa) pode piorar. Por isso a nota e as avaliações entram nos indicadores.

### 3. Dados e evidências
Fontes públicas consultadas pelo grupo em **nov/2026**: Reels do Instagram (58 Reels), Biblioteca de Anúncios do Meta, Google Trends (DF, jan a nov/2026) e Google Maps (unidade 214 Sul). Visualizações medem **exposição**, não compreensão. Ainda **não houve coleta com o público**: a mudança social é um **resultado esperado**, verificado pelos indicadores abaixo. Limites: amostra pequena, classificação manual, sem seguidores e sem dados de quem assistiu.

### 4. Leitura pelo CRISP-DM: o impacto social nas seis etapas
| Etapa | Questão social considerada | Evidência ou decisão do projeto | Risco ou limitação |
|---|---|---|---|
| **1. Compreensão do negócio** | Qual necessidade e quais públicos? Acesso à informação e acessibilidade para clientes e famílias de Brasília, incluindo quem assiste sem som ou não usa Instagram; a equipe também aparece nos vídeos | Objetivo de negócio: mais contatos a partir de Reels que rendem visualizações. Objetivo social: informação clara e resposta ágil (Fase 1 e seções 1 e 2) | Quem pode ficar de fora: pessoas fora do Instagram ou sem som |
| **2. Compreensão dos dados** | Os dados representam os públicos? Só em parte: mostram o conteúdo e a exposição, não quem assistiu | Fontes públicas (Instagram, Biblioteca de Anúncios, Trends e Google Maps), nov/2026, DF e Brasília (seção 3) | Viés de seleção (prints do grid e quem avalia no Google Maps), sem dados do público e sem datas dos posts |
| **3. Preparação dos dados** | Como proteger e tratar os dados? | Sem nomes de usuários nem dados pessoais; só as colunas necessárias; 2 Reels sem visualizações registrados na base e fora do modelo (não descartados em silêncio); temas com poucos posts mostrados com o número de posts | Perda de 2 registros (cerca de 3%) ; classificação manual, revisada pelo grupo, mas ainda subjetiva |
| **4. Modelagem e análise** | Como os resultados variam entre públicos? Comparamos Bessa e Valentina; não há dados para comparar segmentos de público | Erro típico de 2,8x contra 5,5x do chute, com intervalo de confiança (Fase 4); nenhuma característica de pessoas usada no modelo | Conclusão indevida: "ser Bessa ~10x" mistura conteúdo com tamanho da audiência, e associação não é causa |
| **5. Avaliação** | Há benefício social e resultado de negócio? O resultado de negócio foi avaliado pelos critérios da Fase 1; o benefício social é esperado e ainda não foi medido | Critérios de sucesso da Fase 1 atingidos; benefício social a verificar com os indicadores da seção 6 | Efeitos não previstos: mais demanda pode piorar o tempo de espera; publicidade ou avaliação pouco transparente |
| **6. Implantação** | Como acompanhar e corrigir a ação? Indicadores, linha de base, metas, responsáveis e canal de escuta | Campanha "Sabor novo do mês" (Fase 6) e quadro de indicadores (seção 6), com revisão a cada 2 meses | Falta de monitoramento ou de escuta; linhas de base ainda não medidas |

### 5. Ação de inovação social
> Para enfrentar **a informação dispersa e pouco acessível sobre sabores, valores e como reservar**, propomos **um Reel mensal "Sabor novo do mês", com Paulo Bessa, com texto na tela e instrução de como pedir ou reservar, e um canal de resposta e escuta**, nos canais **Instagram, Facebook e WhatsApp**, voltados a **clientes e famílias de Brasília, incluindo quem assiste sem som ou não usa Instagram**. Ela pode contribuir para **gerar mais contatos e reservas a partir do tipo de Reel que já sabemos que rende visualizações** e gerar **acesso a informação clara e a um atendimento que responde**. Para reduzir **o risco de exposição de imagem e de dados pessoais e de avaliações ou publicidade pouco transparentes**, adotaremos **autorização de imagem, dúvidas individuais só no WhatsApp, #publi nas parcerias e nenhuma troca de brinde por avaliação**.

| Elemento | Proposta |
|---|---|
| **O que será feito** | (a) Reel mensal do sabor novo com valor e como pedir ou reservar em texto na tela e na legenda. (b) Canal de escuta: responder comentários, WhatsApp e avaliações do Google Maps (inclusive as negativas) em um prazo definido. (c) Regras de transparência: #publi, nenhum brinde por avaliação e autorização de imagem |
| **Para quem** | Clientes e famílias de Brasília, pessoas com barreiras de acesso ao conteúdo e a equipe |
| **Canal** | Instagram e Facebook (Reel e anúncio), WhatsApp e Google Maps |
| **Recursos** | A equipe que já produz os Reels; a verba de anúncio já existente, realocada de um dos 4 anúncios parados (sem verba extra); tempo de quem atende o WhatsApp |
| **Responsáveis** | Funções propostas, a confirmar com a pizzaria: responsável pelo marketing, pelo atendimento e pela gerência da unidade |
| **Prazo** | Linha de base em 30 dias; depois, o primeiro Reel revisado; revisão a cada 2 meses |

### 6. Indicadores e validação
Visualizações, alcance e cliques mostram **exposição**, e não provam impacto social sozinhos. Por isso, os indicadores 2 e 3 medem **mudança para o público** (compreensão e conclusão de uma tarefa).

| Indicador | O que será medido | Como será calculado | Linha de base e meta | Fonte e periodicidade | Responsável |
|---|---|---|---|---|---|
| **1. Acesso** (acessibilidade do conteúdo) | Reels de sabor novo com texto na tela e instrução de como pedir ou reservar | Reels com os dois itens ÷ total de Reels de sabor novo × 100 | Base: hoje 18 de 35 Reels da Bessa têm texto na tela (51%); a instrução de reserva ainda não foi checada. Meta proposta: 100% | Planilha de acompanhamento dos posts, a cada Reel publicado | Responsável pelo marketing |
| **2. Experiência** (compreensão) | Pessoas que entendem o sabor e como reservar depois de ver o Reel | Mini-teste com 2 perguntas (qual é o sabor? como reservo ou peço?): % que acerta as duas, informando o tamanho do grupo | Base: aplicar com o Reel atual, antes da mudança. Meta proposta: aumentar em relação à base com a versão revisada | Teste com grupo de clientes ou colegas, antes e depois da revisão | Responsável pelo marketing, com apoio do grupo no 1º teste |
| **3. Resultado** (conclusão de tarefa) | Pessoas que pedem informação no WhatsApp e concluem a reserva ou o pedido | Conversas que terminam em reserva ou pedido ÷ conversas iniciadas × 100, e tempo médio da primeira resposta | Base: medir 30 dias antes da campanha. Meta proposta: aumentar a conclusão e reduzir o tempo de resposta | Estatísticas do WhatsApp Business, mensal | Responsável pelo atendimento |
| **4. Experiência de atendimento** (prova social) | Satisfação e reclamações recentes | Nota média no Google Maps e % de novas avaliações que citam espera ou atendimento | Base: nota 4,4 em 5.561 avaliações; % de menções a medir. Meta proposta: manter 4,4 ou mais e reduzir as menções negativas | Google Maps, mensal | Gerência da unidade |
| **5. Negócio** | Custo por contato | Gasto do anúncio ÷ cliques em WhatsApp ou ligação | Base: anúncios atuais. Meta: ficar abaixo deles | Gerenciador de Anúncios, a cada ciclo de 7 dias | Responsável pelos anúncios |

**Primeira medição.** Como ainda não houve coleta com o público, a primeira medição será a linha de base: (1) listar os Reels existentes e contar quantos têm texto na tela e instrução de como pedir ou reservar; (2) aplicar o mini-teste de 2 perguntas ao Reel atual para um grupo de clientes ou colegas (sugerimos cerca de 20 pessoas, informando o tamanho do grupo); (3) registrar 30 dias de WhatsApp e de avaliações antes de mudar qualquer coisa. Depois, repetir as mesmas medidas com a versão revisada. As metas acima são **propostas** a ajustar depois de medir a linha de base.

### 7. Limites e acompanhamento
Ainda precisa ser verificado: as linhas de base, se o público entende melhor o Reel revisado, se o efeito de Paulo Bessa é real (teste A/B da Fase 6). **Ajustar** se, após 2 ciclos, o custo por contato não ficar abaixo dos anúncios atuais ou a compreensão não melhorar. **Rever ou interromper** se a nota cair abaixo de 4,4 por mais menções à espera ou ao atendimento, ou se houver reclamação sobre uso de imagem ou publicidade sem identificação.

---

## 📁 Arquivos
* `crispdm_pizza_bessa.ipynb`: análise completa, com os dados já dentro dele (abra no Google Colab e use Executar tudo; não precisa subir arquivo)
* `posts_instagram.xlsx`: a mesma base dos Reels em planilha (opcional; abas Posts, Resumo, Contexto e Dicionario)

## 👥 Autores
Pedro Henrique Nobre de Araujo, Mell Lima, Daniel Câmara, Rodrigo Avelar, Pedro Lucas e Nicolas Balzon
