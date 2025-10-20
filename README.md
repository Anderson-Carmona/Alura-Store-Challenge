# Alura-Store-Challenge
Discernimento
Análise de Desempenho de Lojas
Descrição do Projeto
Este projeto analisa dados de vendas de quatro lojas (Loja 1, Loja 2, Loja 3, Loja 4) para identificar padrões de desempenho, produtos mais/menos vendidos, avaliações de clientes, faturamento e distribuição geográfica. O objetivo é recomendar qual loja deve ser vendida, com base em métricas quantitativas e qualitativas.
________________________________________
Estrutura do Projeto
 Copiar
projeto_analise_lojas/
│
├── dados/
│   ├── loja_1.csv
│   ├── loja_2.csv
│   ├── loja_3.csv
│   └── loja_4.csv
│
├── resultados/
│   ├── relatorio_final.md
│   ├── mapa_vendas_loja1.html
│   └── heatmap_vendas_loja3.html
│
├── scripts/
│   ├── analise_dados.py
│   └── gerar_graficos.py
│
└── README.md
________________________________________
Ferramentas Utilizadas
•	Python: Para processamento de dados e geração de gráficos. 
o	Bibliotecas: pandas, matplotlib, seaborn, folium, geopandas.
•	Excel/Google Sheets: Para análise exploratória e visualizações rápidas.
•	Google Earth: Para visualização geográfica interativa (opcional).
________________________________________
Análises Realizadas
1.	Produtos Mais e Menos Vendidos:
o	Identificação dos produtos com maior e menor volume de vendas em cada loja.
o	Visualização: Gráficos de barras.
2.	Faturamento Total por Loja:
o	Cálculo do faturamento (soma de preço + frete) para cada loja.
o	Visualização: Gráfico de barras ou pizza.
3.	Avaliações Médias dos Clientes:
o	Cálculo da média de avaliações por loja e por região.
o	Visualização: Gráfico de barras ou mapa coroplético.
4.	Frete Médio por Loja/Região:
o	Análise do custo médio de frete e seu impacto na competitividade.
o	Visualização: Gráfico de dispersão ou mapa.
5.	Análise Geográfica (Extra):
o	Mapeamento das vendas usando coordenadas de latitude/longitude.
o	Visualização: Mapas interativos (Folium) ou gráficos de dispersão (Matplotlib).
________________________________________
Insights Principais
•	Loja 3 se destaca como a melhor opção para venda, devido ao: 
o	Maior faturamento total.
o	Produtos populares ("Kit banquetas").
o	Melhor média de avaliações dos clientes.
o	Frete médio mais baixo.
•	Distribuição geográfica: 
o	Concentração de vendas no Sudeste (SP, RJ) para a Loja 1.
o	Vendas dispersas para a Loja 2, sem clusters evidentes.
o	Alto faturamento no Centro-Oeste (GO, DF) para a Loja 3.
________________________________________
Como Reproduzir a Análise
1.	Instalar dependências:
bash
 Copiar
pip install pandas matplotlib seaborn folium geopandas
2.	Executar os scripts:
o	analise_dados.py: Processa os dados e calcula métricas.
o	gerar_graficos.py: Gera visualizações (gráficos e mapas).
3.	Visualizar resultados:
o	Os gráficos e mapas serão salvos na pasta resultados/.
o	Abra os arquivos .html (mapas interativos) em um navegador.
________________________________________
Exemplo de Código
Gráfico de Dispersão Geográfica
python
 Copiar
import matplotlib.pyplot as plt

# Carregar dados de uma loja
loja = pd.read_csv('dados/loja_1.csv')

# Plotar dispersão
plt.figure(figsize=(10, 8))
plt.scatter(loja['lon'], loja['lat'], alpha=0.5, c='blue', s=10)
plt.title('Distribuição Geográfica das Vendas - Loja 1')
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.grid(True)
plt.savefig('resultados/dispersao_loja1.png')
plt.show()
Mapa Interativo com Folium
python
 Copiar
import folium
from folium.plugins import HeatMap

# Criar mapa
mapa = folium.Map(location=[-14.2350, -51.9253], zoom_start=4)

# Adicionar pontos de venda
for idx, row in loja.iterrows():
    folium.CircleMarker(
        location=[row['lat'], row['lon']],
        radius=2,
        color='blue',
        fill=True
    ).add_to(mapa)

# Adicionar heatmap
HeatMap(loja[['lat', 'lon']].values).add_to(mapa)

# Salvar mapa
mapa.save('resultados/heatmap_loja1.html')
________________________________________
Próximos Passos
•	Explorar estratégias para melhorar o desempenho das lojas com menor faturamento.
•	Investigar a correlação entre frete, avaliações e localização geográfica.
•	Automatizar a geração de relatórios para atualizações periódicas.
________________________________________
Autor: Anderson Carmona Data: Outubro de 2025
