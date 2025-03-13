Qual o produto mais vendido?
Os dados de vendas incluem colunas como SKU, nome do produto, quantidade vendida e plataforma (AliExpress, Etsy, Shopee). Agora, vou calcular o produto mais vendido somando as quantidades vendidas em todas as plataformas. ​
import pandas as pd

# Caminhos dos arquivos
files = {
    "AliExpress": "/mnt/data/Meganium_Sales_Data_-_AliExpress.csv",
    "Etsy": "/mnt/data/Meganium_Sales_Data_-_Etsy.csv",
    "Shopee": "/mnt/data/Meganium_Sales_Data_-_Shopee.csv",
}

# Carregar os dados
dataframes = {platform: pd.read_csv(path) for platform, path in files.items()}

# Exibir as primeiras linhas de cada dataset para inspeção
{platform: df.head() for platform, df in dataframes.items()}

O produto mais vendido foi o NEW MEGANIUM RG 40XXV, com um total de 41 unidades vendidas nas três plataformas (AliExpress, Etsy e Shopee)
# Consolidar todas as vendas em um único DataFrame
all_sales = pd.concat(dataframes.values())

# Agrupar por produto e somar as quantidades vendidas
top_product = all_sales.groupby("product_sold")["quantity"].sum().idxmax()
top_quantity = all_sales.groupby("product_sold")["quantity"].sum().max()

top_product, top_quantity



Para melhorar sua logística, vou analisar os seguintes aspectos:  

1. **Países com maior demanda** – Para entender onde concentrar estoques e otimizar frete.  
2. **Plataformas com mais vendas** – Para identificar onde focar esforços de distribuição.  
3. **Produtos mais vendidos por plataforma** – Para entender preferências do público em cada canal.  
4. **Descontos aplicados** – Para verificar o impacto das promoções.  

Vou calcular esses dados agora.

Aqui estão algumas análises que podem ajudar a melhorar sua logística:  

### 1. **Países com maior demanda**  
- **Canadá** (46 unidades)  
- **França** (36 unidades)  
- **Austrália** (28 unidades)  
- **Japão** (27 unidades)  
- **Alemanha** (23 unidades)  

🔹 **Sugestão:** Se houver depósitos ou centros de distribuição, priorize estoques nesses países para reduzir prazos e custos de envio.  

### 2. **Plataformas com mais vendas**  
- **Shopee** (64 unidades)  
- **AliExpress** (58 unidades)  
- **Etsy** (56 unidades)  

🔹 **Sugestão:** Como a Shopee lidera em vendas, talvez valha investir mais em logística nessa plataforma (faster shipping, fulfillment centers).  

### 3. **Produtos mais vendidos por plataforma**  
- **AliExpress**: Destaque para "NEW MEGANIUM RG35XX" (14 unidades) e "NEW MEGANIUM RG28XX" (13 unidades).  
- **Etsy**: O "NEW MEGANIUM RG 40XXV" tem melhor desempenho (17 unidades).  
- **Shopee**: O "NEW MEGANIUM RG CubeXX" domina (18 unidades).  

🔹 **Sugestão:** Considere personalizar estoques por plataforma, enviando mais unidades de cada produto para os marketplaces onde têm melhor desempenho.  

### 4. **Impacto dos descontos**  
- **Maior desconto médio:** Shopee (**$58,54** por venda)  
- **Etsy:** $41,56 por venda  
- **AliExpress:** $37,43 por venda  

🔹 **Sugestão:** O alto desconto na Shopee pode indicar que os clientes são mais sensíveis a preços. Teste estratégias como frete grátis em vez de descontos diretos.  

Se precisar de mais detalhes ou um plano mais específico, posso refinar a análise! 🚀
