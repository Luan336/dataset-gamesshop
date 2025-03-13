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
