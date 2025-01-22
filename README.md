# Sentinela



## Como Começar

Para facilitar o início do GitLab, aqui está uma lista das próximas etapas recomendadas.

Já é um profissional? Basta editar este README.md e torná-lo seu. Quer facilitar? [Use o modelo na parte inferior](#editing-este-leia-me)!


## Adiciona em seus arquivos

- [ ] [Create](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#create-a-file) or [upload](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#upload-a-file) files
- [ ] [Add files using the command line](https://docs.gitlab.com/ee/gitlab-basics/add-file.html#add-a-file-using-the-command-line) or push an existing Git repository with the following command:

```
cd existing_repo
git remote add origin https://gitlab.com/projetos_ciencia_dados/sentinela.git
git branch -M main
git push -uf origin main
```


# ⭐ Análise de Dados e Detecção de Sites Phishing com Data Science (e Aprendizado de Máquina)

## Introdução
Existe na internet muitos sites de phishing, que são sites fraudulentos, sites que aparentam ser legítimos, sites que são cópias de outros sites originais, vocês já devem ter conhecido alguém que foi vítima desses golpes. A intenção é enganar o usuário e roubar Dados que são considerados super valiosos. Sites assim são uma ameaça significativa para indivíduos e organizações, alguns ataques são baseados como similaridade de URL, homógrafo, punycode, homófono, bit squatting e combosquatting, isso são apenas algumas técnicas que podem ser usadas para criar sites phishing, devemos nos atentar e tomar cuidado ao realizar compras online, fornecer dados pessoais, conectar ou criar contas nos sites. Além de sites, existem emails, mensagens, SMS, e etc…, mas vamos focar nos sites hoje.

Foi desenvolvido um dataset [https://archive.ics.uci.edu/dataset/967/phiusiil+phishing+url+dataset](url) em 2023 com cerca de 233.579 dados com 54 características de sites legítimos e sites de phishing, sendo 134.580 sites legítimos e 100.945 sites phishing. Resolvi usar esse conjunto de dados para realizar uma análise de dados buscando identificar padrões e insights poderosos e usar técnicas de machine learning para criar e treinar um algoritmo de classificação.


## Escolha dos Algoritmos para o Problema de Classificação

### Random Forest:
- Robusto para datasets com muitas características.
- Lida bem com dados categóricos e numéricos.
- Oferece uma métrica de importância das variáveis.

### LightGBM (ou XGBoost, dependendo da preferência):
- Algoritmo baseado em árvores de decisão com boosting.
- Excelente para problemas de classificação com grande volume de dados.
- Alta eficiência e flexibilidade para ajuste fino.

## Insights do Dataset
1. **Nossos dados não possuem valores nulos** e encontramos as seguintes características de descrição:
   - Possuímos 425 URLs iguais, todas se repetem duas vezes (bem estranho).
   - 15.709 domínios são usados mais de uma vez para diferentes URLs.
   - Temos uma minoria, menor que 1% de TLD (extensão de domínios) únicos.
   - Existem 37.921 títulos repetidos entre os sites.
   - O domínio mais frequente é o “ipfs.io“ ocorre 1.197 vezes.
   - A extensão de domínio mais usada é “.com“ com 112.554 usos.
   - O título mais frequente é “0“ com 32.719 ocorrências.

2. **Similaridade das URLs**: Temos uma média de 78% de similaridade entre URLs que sabemos que são legítimas e URLs duvidosas.
3. **Comprimento das URLs**: A menor URL tem 13 caracteres e estranhamente a maior tem 6097 caracteres. 75% (176.846) das URLs tem 34 caracteres ou menos.
4. **Distribuição de Comprimentos**: Através do gráfico BoxPlot notamos que comprimentos maiores de URLs estão mais distribuídos a sites de phishing, e o gráfico nos mostrou que a maior URL descrita no insight 3 é na verdade um site phishing, pois ela é um outlier.
5. **HTTPS vs. Phishing**: Observamos que 30% dos sites com HTTPS são phishing e 70% são legítimos, e 90% dos sites sem HTTPS são phishing.
6. **Categorias Específicas**: Sites entre as categorias Banco, Criptos e Pagamentos raramente são sites de phishing em nossa base dados:
   - Apenas 6.02% dos sites de pagamentos são phishing.
   - 5.43% dos sites de banco são phishing.
   - 0.60% dos sites de cripto são phishing.
7. **Links para Redes Sociais**: Observamos que existe uma forte correlação negativa entre sites phishing e sites que têm links para redes sociais, o que indica que quanto mais links de redes sociais em um site, menor a chance dele ser phishing.
8. **Proporção de Letras nas URLs**: De fato, a proporção de letras contidas em uma URL é fator diferencial entre sites phishing ou legítimos.
9. **Referências Externas**: O número de referências externas no site tem um grande impacto com a indicação de que um site é ou não phishing.

## Relevância do Conjunto para o Aprendizado de Máquina
- **Classificar o Conteúdo Básico da Página**: Analisando o conteúdo da página da web (HasTitle, HasDescription, URLTitleMatchScore).
- **Construção de um Classificador**: Pode ser construído um classificador de floresta aleatória para prever se uma URL é phishing ou não.
- **Avaliação de Sites**: Esses dados podem ser usados para avaliar se os sites são phishing ou não (IsHTTPS, HasPasswordField, Banco, Criptografia, etc…).
- **Níveis de Segurança**: Analisando os níveis de segurança dos sites, detectando sites de baixa segurança (HasObfuscation, NoOfSelfRedirect, IsDomainIP).
- **Desempenho de SEO**: Analisar o desempenho de SEO de sites e fornecer sugestões de melhoria (HasTitle, HasDescription, DomainTitleMatchScore).
- **Usabilidade do Site**: Pode ser usado para prever se o site é fácil de usar (IsResponsive, NoOfPopup, NoOfSelfRef).
- **Risco de Fraude**: Prever se a página da web representa um risco de fraude (IsDomainIP, NoOfObfuscatedChar, Bank, Pay).


## Status Projeto
- **Concluído
