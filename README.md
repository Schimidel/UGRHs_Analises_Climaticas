# UGRH Paraná - Análise de Precipitação e Temperatura

Este repositório contém o workflow de análise climática para a **Unidade de Gestão de Recursos Hídricos (UGRH) Paraná**. O objetivo é analisar dados históricos e projeções de precipitação e temperatura, permitindo a extração de anomalias, ciclos de periodicidade via Wavelets (Ondulas) e regressões de tendência futura. 

Todo o workflow desenvolvido pode ser adaptado e replicado para outras UGRHs ou bacias hidrográficas.

---

## 📂 Estrutura do Repositório e Notebooks

Os notebooks estão divididos em etapas lógicas do fluxo de trabalho:

### 1. Preparação e Pré-processamento
* **[`Download_Dados.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Download_Dados.ipynb)**: Scripts para baixar e organizar os dados climáticos históricos e de projeções.
* **[`Mapa_UGRH_PARANA.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Mapa_UGRH_PARANA.ipynb)**: Delimitação espacial e geração de mapas da bacia de interesse usando GeoPandas e Cartopy.
* **[`Dados_CESMLENS.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Dados_CESMLENS.ipynb)**: Processamento e tratamento específico dos dados de temperatura e precipitação do grande conjunto de dados do modelo CESM-LENS.

### 2. Análise Climatológica Histórica (AV1 / ATV1)
* **[`Precipitacao_Historico.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Precipitacao_ATV1.ipynb)** e **[`Temperatura_Historico.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Temperatura_AV1.ipynb)**: Primeiras análises estatísticas exploratórias e cálculo das climatologias históricas de referência.

### 3. Análise de Frequências (Wavelets)
* **[`Atividade_Wavelets_Precipitação.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Atividade_Wavelets_Precipitação.ipynb)**: Análise wavelet contínua (CWT) da anomalia de precipitação (NCEP e GPCC), bruta e desestacionalizada.
* **[`Atividade_Wavelets_Temperatura.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Atividade_Wavelets_Temperatura.ipynb)**: Análise wavelet contínua (CWT) para séries de temperatura (NCEP e NOAA), identificando ciclos dominantes (anuais, interanuais).

### 4. Projeções de Mudanças Climáticas (CMIP5)
* **[`Projeções_Futuras_Precipitação.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Projeções_Futuras_Precipitação.ipynb)**: Compara as tendências históricas de chuva com projeções futuras (2100) para os cenários RCP4.5 e RCP8.5 usando modelos como CCSM4, ACCESS1-3 e HadGEM2-ES.
* **[`Projeções_Futuras_Temperatura.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Projeções_Futuras_Temperatura.ipynb)**: Compara tendências de aquecimento e anomalias de temperatura nos mesmos cenários futuros de emissão.
* **[`Correlação entre anomalias.ipynb`](file:///c:/Users/gabri/Downloads/UGRH/Correlação%20entre%20anomalias.ipynb)**: Análise estatística de correlação cruzada e espacial entre as diferentes anomalias.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

As principais ferramentas em Python utilizadas nas análises são:
- **`xarray`**: Manipulação eficiente de grades netCDF multidimensionais.
- **`pycwt`**: Execução de transformada rápida de wavelet contínua e testes estatísticos associados.
- **`statsmodels`**: Decomposição sazonal de séries temporais.
- **`geopandas` & `shapely`**: Manipulação de dados geoespaciais e formatos shapefiles.
- **`cartopy`**: Criação de mapas geoespaciais e projeções cartográficas.
- **`matplotlib` & `pandas`**: Manipulação e plotagem gráfica de dados tabulares.

---

## 🚀 Como Executar

### 1. Requisitos Locais
Certifique-se de possuir o Python instalado. Recomenda-se criar um ambiente virtual e instalar as dependências:
```bash
python -m venv .venv
source .venv/bin/activate  # No Windows use: .venv\Scripts\activate
pip install -r requirements.txt
```
*(Nota: Os notebooks possuem células automáticas de instalação de dependências para rodar diretamente no Google Colab).*

### 2. Dados de Entrada
Os notebooks dependem de arquivos climáticos contidos na pasta `./Dados/` (por exemplo, arquivos `.nc` contendo os históricos e projeções de modelos como CCSM4, GPCC, NOAA, etc.).

DOI: 10.5281/zenodo.21497632

