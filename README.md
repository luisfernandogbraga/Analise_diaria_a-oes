# Análise de Rentabilidade de Ações
![bolsa-werther-santana-estadao_210320204824](https://github.com/luisfernandogbraga/Analise_diaria_a-oes/assets/134460985/5d5e714f-1408-4fd2-b005-26e162f9b735)



Exemplo de como realizar uma análise de rentabilidade de ações usando Python e a biblioteca yfinance para obter os dados históricos de uma ação listada na B3. Neste exemplo, estamos usando a ação "IRDM11.SA". O objetivo é plotar um gráfico dos preços de fechamento ajustados ao longo do tempo e calcular a rentabilidade total do período.

# Pré-requisitos

Certifique-se de ter as seguintes bibliotecas instaladas em seu ambiente Python:
yfinance
pandas
matplotlib

Você pode instalá-las usando o seguinte comando: pip install yfinance pandas matplotlib

# Como Usar
Importe as bibliotecas necessárias:
import yfinance as yf
import pandas as pd
import matplotlib.pyplot as plt

Defina o ticker da ação desejada e o intervalo de datas:
ticker = "IRDM11.SA"
start_date = "2023-01-01"
end_date = "2023-08-10"

Obtenha os dados históricos da ação usando a biblioteca yfinance:
data = yf.download(ticker, start=start_date, end=end_date)

Calcule a rentabilidade diária e total do período:
data['Daily_Return'] = data['Adj Close'].pct_change()
total_return = (data['Adj Close'][-1] / data['Adj Close'][0]) - 1

Plote o gráfico dos preços de fechamento ajustados:
plt.figure(figsize=(20, 10))
plt.plot(data['Adj Close'])
plt.title(f"Preços de Fechamento Ajustados de {ticker}")
plt.xlabel("Data")
plt.grid(True)

Adicione os valores de preço nas linhas do gráfico:
spacing = 2
for index, value in enumerate(data['Adj Close']):
    if index % spacing == 0:
        plt.annotate(f'{value:.2f}', (data.index[index], value), textcoords="offset points", xytext=(0,10), ha='left')

Exiba a rentabilidade total do período fora do gráfico:
plt.annotate(f'Rentabilidade Total do Período: {total_return:.2%}',
             xy=(1, 0), xycoords='axes fraction',
             xytext=(-10, 10), textcoords='offset points',
             ha='right', va='bottom')

Mostre o gráfico:
plt.show()

# Resultado
O código acima irá gerar um gráfico dos preços de fechamento ajustados da ação ao longo do tempo, destacando os valores de preço em intervalos regulares e exibindo a rentabilidade total do período fora do gráfico.

Lembre-se de que este é um exemplo básico e que análises mais aprofundadas podem ser realizadas com técnicas adicionais e considerações sobre dados financeiros.

Sinta-se à vontade para adaptar este exemplo para suas próprias análises de ações e adicionar mais informações relevantes ao README conforme necessário.

<p align="center">
<img loading="lazy" src="http://img.shields.io/static/v1?label=STATUS&message=FINALIZADO&color=BLUE&style=for-the-badge"/>
</p>







