# Porsche Sales Intelligence — Dashboard de Vendas

Dashboard interativa em HTML, CSS e JavaScript puro, criada para o desafio da DIO. O objetivo é transformar uma planilha de 100 vendas em uma visão executiva simples de explorar, com filtros, indicadores e perguntas de negócio claras.

## 🔎 Perguntas de negócio

1. **Quais modelos concentram mais receita?**  
   A receita somada por modelo ajuda a identificar quais modelos mais contribuem para o faturamento observado. O gráfico mostra os oito primeiros modelos no recorte atual. Receita não é lucro: a base não traz custos ou margens.

2. **Como os clientes pagam?**  
   A distribuição por método de pagamento mostra a quantidade e a participação de cada forma de pagamento. Isso ajuda a observar a composição dos pagamentos na amostra, sem afirmar causalidade ou preferência de mercado.

3. **Qual é a situação das entregas?**  
   A distribuição de status permite distinguir vendas entregues, canceladas e as que ainda aparecem em outras etapas. É útil para levantar pontos de acompanhamento operacional. Os status originais sanitizados são mantidos separados para não esconder diferenças entre etapas.

## 📌 Indicadores e filtros

- **Indicadores:** total de vendas no recorte, receita bruta, ticket médio e participação de vendas entregues.
- **Filtros:** modelo, cidade, estado, ano do veículo e método de pagamento.
- **Detalhamento:** tabela filtrável com data sanitizada, modelo, ano do veículo, preço, cidade/UF, método de pagamento e status.
- Os filtros atualizam os indicadores e todos os gráficos na hora. “Limpar filtros” restaura a base completa.

## 🧹 Tratamento dos dados

A planilha de origem contém versões cruas e sanitizadas de vários campos. Para a dashboard foram usadas apenas as colunas sanitizadas:

| Campo no HTML | Coluna usada na planilha |
|---|---|
| `sale_date` | `SaleDateSanitized` |
| `model` | `PorscheModelSanitized` |
| `model_year` | `ModelYearSanitized` |
| `price` | `SalesPriceSanitized` |
| `mileage` | `VehicleMileageSanitized` |
| `payment_method` | `PayMethodSanitized` |
| `city` | `CitySanitized` |
| `state` | `StateSanitized` |
| `delivery_status` | `DeliveryStatusSanitized` |

- Preço, ano do veículo e quilometragem foram tratados como valores numéricos.
- As datas foram preservadas como texto sanitizado para não inventar datas válidas: registros com `INVALID` ou data ausente continuam identificáveis no detalhamento.
- Campos pessoais, como nome do cliente e vendedor, foram excluídos do HTML.
- Os dados necessários para os gráficos ficam embutidos no arquivo `index.html`; não há servidor, API ou dependências externas.
- A base contém 100 registros. Os totais e gráficos refletem os valores fornecidos; não se presumem custos, margens ou outros dados que não estão na planilha.

## 🧠 Prompt de construção e refinamento

**Prompt inicial usado como especificação:**

> Crie uma dashboard de vendas Porsche em um único arquivo `index.html`, usando HTML, CSS e JavaScript puro. Use somente as colunas sanitizadas da planilha. Faça uma interface responsiva com identidade visual premium inspirada na Porsche, fundo escuro, detalhes vermelhos e tipografia limpa. Inclua filtros por modelo, cidade, estado, ano do veículo e método de pagamento; KPIs de total de vendas, receita, ticket médio e entregues; e três análises: receita por modelo, distribuição de métodos de pagamento e status de entrega. Todos os filtros devem atualizar todos os KPIs e gráficos. Inclua tabela de detalhamento, estado vazio para filtros sem resultados, botão para limpar filtros e comentários de interpretação que não confundam receita com lucro. Não inclua nomes de clientes ou vendedores, não invente valores e não dependa de backend nem de bibliotecas externas.

**Refinamentos aplicados na versão final:**

- Escolha explícita de perguntas de negócio em vez de gráficos sem objetivo.
- Inclusão de estados vazios, rótulos acessíveis e layout responsivo para celular.
- Explicitação de que receita não significa lucro.
- Manutenção dos status de entrega separados, evitando agregar etapas operacionalmente diferentes.
- Exclusão de dados pessoais e preservação das datas sanitizadas sem corrigir silenciosamente valores inválidos.

> Se você usar outra ferramenta para modificar este projeto, atualize esta seção para descrever o prompt real e as mudanças que você fizer. A documentação deve refletir o processo efetivamente realizado.

## 🛠️ Tecnologias

- HTML5
- CSS3 (layout responsivo)
- JavaScript puro (filtros, agregações e renderização)
- Excel como fonte de dados

## ▶️ Como executar localmente

1. Baixe ou clone este repositório.
2. Abra `index.html` no navegador. Não é necessário instalar pacotes ou iniciar um servidor.
3. Se alterar o HTML, atualize o arquivo e recarregue a página.

## 🌐 Como publicar com GitHub Pages

1. Crie um repositório **público** na sua conta GitHub, com nome legível, por exemplo `porsche-sales-dashboard`.
2. Envie `index.html` e `README.md` para a raiz do repositório.
3. No GitHub, entre em **Settings → Pages**.
4. Em **Build and deployment**, selecione **Deploy from a branch**.
5. Escolha a branch `main` e a pasta `/(root)`; clique em **Save**.
6. Aguarde a publicação. O endereço normalmente será `https://SEU-USUARIO.github.io/porsche-sales-dashboard/`.
7. Abra o link publicado e teste cada filtro, o botão de limpar filtros e a tabela.
8. No README, substitua o endereço de exemplo pelo link real da sua dashboard depois de publicar.

**Importante:** os arquivos deste pacote estão preparados localmente; a publicação precisa ser feita no seu GitHub. Não informe um link como publicado antes de testar a URL real.

## ✅ Checklist de entrega

- [ ] Repositório público na sua conta
- [ ] `index.html` e `README.md` na raiz
- [ ] GitHub Pages habilitado
- [ ] Filtros e botão de reset testados
- [ ] Print da dashboard com um filtro aplicado adicionado ao README (opcional, mas recomendado)
- [ ] Link real da dashboard adicionado ao README
- [ ] Revisão final para garantir que nenhum dado pessoal foi incluído

## 📷 Evidências para o portfólio

Recomendação: capture um print da visão geral e outro após aplicar um filtro (por exemplo, um modelo específico). Inclua as imagens no repositório, numa pasta `assets/`, e faça referência a elas no README. Isso demonstra não só a aparência, mas também o funcionamento da interação.
