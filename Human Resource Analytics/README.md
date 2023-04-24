# Human Resource Analytics

Neste projeto cobrindo todas as etapas de um projeto real de Data Science pude resolver o problema de como utilizar dados para responder a questões importantes para permitir que uma empresa tenha conhecimento sobre:

 - **Quais são os fatores que influenciam para um colaborador deixar a empresa?**

 - **Como reter pessoas?**

 - **Como antecipar e saber se um determinado colaborador vai sair da empresa?**

E por fim disponibilizar recursos para que a empresa consiga realizar a predição para verificar se um colaborador vai ou não deixar a empresa com base em atributos como comportamento e carga de trabalho, nível de satisfação com a empresa e resultados de performance.

---

### Estrutura

![estrutura](https://user-images.githubusercontent.com/14170425/234126087-713c469a-9a82-4457-bf09-afbcd5736e9e.png)

Para resolver esse problema foi construído uma solução completa para armazenamento, gestão e automatização de fluxos de dados utilizando tecnologias como **Apache Airflow**, **Docker** e **Minio** além de explorar uma suíte de tecnologias para trabalhar com Análise de Dados e Machine Learning que são: **Pandas**, **Scikit-learn**, **Pycaret**, **SweetViz**, **Streamlit**.

<img width="593" alt="tecnologias" src="https://user-images.githubusercontent.com/14170425/234127619-ecaafbbf-0e0c-4f1b-84ec-37cd34a20a06.png">

Depois da infraestrutura devidamente criada e configurada, levando em consideração o desafio proposto foram criados e modelados atributos relevantes para análise utilizando fontes de dados diversas como arquivos em formato xlsx, json e dados no Sistemas de Gerenciamento de Banco de Dados MySQL.

O projeto foi então dividido da seguinte forma:

 - Coleta dos dados das difentes fontes (MySQL, json e csv);
 - Criação do DataLake utilizando Minio;
 - Modelagem dos dados e criação de atributos como Departamento e Salário;
 - Análise exploratória de dados;
 - Orquestração e junção dos dados para o Minio utilizando o Airflow;
 - Desenvolvimento do modelo de Machine Learning;
 - Deploy da aplicação via Streamlit, ligado a base final e ao modelo de predição;

---

### Resultados

Na etapa de Análise Exploratória de Dados foram descobertos os vários insights importantes abaixo:

 - A empresa tem uma rotatividade de 24%.
 
 - Podemos assumir que os empregados que mais deixam a empresa estão menos satisfeitos.
 
 - Existe um valor considerável de empregados insatisfeitos.<br>
 ![2023-04-24_20-05](https://user-images.githubusercontent.com/14170425/234134564-c715cdcf-8f7b-43f7-a416-d0a4ad6cbd58.png)

 - A maioria dos empregados que saíram tinha salário baixo ou médio.
 ![image](https://user-images.githubusercontent.com/14170425/234133743-e440a5e3-74e2-4228-8bd7-7469cde123e0.png)

 - Os departamentos de vendas, técnico e suporte são top 3 departamentos com maior índice de turnover.
![image](https://user-images.githubusercontent.com/14170425/234133791-19331907-59cd-4ce2-bd24-bf9440321142.png)

 - Todos os empregados que estavam inseridos sem muitos projetos deixaram a empresa.
![image](https://user-images.githubusercontent.com/14170425/234133840-cef95bb7-562e-42b7-b92a-ec583ad7db6b.png)

 - Colaboradores com baixa performance tendem a deixar a empresa.
![image](https://user-images.githubusercontent.com/14170425/234134004-318bfa26-2ca8-41a8-bf6d-d83a7736ea77.png)

 - Colaboradores insatisfeitos com a empresa têm uma maior tendência para evadir.
![image](https://user-images.githubusercontent.com/14170425/234133938-67773db8-6f34-4a3f-a70f-27996b4b7b57.png)

 E quando comparamos o número de projetos com a nota de avaliação do empregado:
 
 - Há um aumento na avaliação para os funcionários que realizaram mais projetos dentro do grupo de quem deixou a empresa.
 - Para o grupo de pessoas que permaneceram na empresa, os empregados tiveram uma pontuação de avaliação consistente, apesar do aumento nas contagens de projetos.
 - Empregados que permaneceram na empresa tiveram uma avaliação média em torno de 70%, mesmo com o número de projetos crescendo.
 - Esta relação muda drasticamente entre os empregados que deixaram a empresa. A partir de 3 projetos, as médias de avaliação aumentam consideravelmente.
 - Empregados que tinham dois projetos e uma péssima avaliação saíram.
 - Empregados com mais de 3 projetos e avaliações altas deixaram a empresa.

 ![image](https://user-images.githubusercontent.com/14170425/234136420-cfd776b9-790f-4bfb-a95e-4edaa164f662.png)
 
 

Através da análise foi possível desenvolver 3 grupos distintos para agrupar colaboradores que deixaram a empresa por comportamentos
similares que são:

 - **Grupo 1 (Empregados insatisfeitos e trabalhadores)**: A satisfação foi inferior a 20 e as avaliações foram superiores a 75. Que corresponde ao grupo de funcionários que deixaram a empresa e eram bons trabalhadores, mas se sentiam péssimos no trabalho.
 - **Grupo 2 (Empregados ruins e insatisfeitos)**: Satisfação entre 35 à 50 e as suas avaliações abaixo de ~ 58. Corresponde aos empregados que foram mal avaliados e se sentiram mal no trabalho.
 - **Grupo 3 (Empregados satisfeitos e trabalhadores)**: Representa os empregados ideais, que gostam do seu trabalho e são bem avaliados por seu desempenho. Este grupo pode indicar os empregados que deixaram a empresa porque encontraram outra oportunidade de trabalho.
 
 ![clusters](https://user-images.githubusercontent.com/14170425/234129678-2462e4f9-45b9-4207-80fc-f99794c15be2.png)


Para a estimativa com o objetivo de predizer se um empregado vai deixar a empresa foi implementado um modelo utilizando o algoritmo **Gradient Boosting Classifier** que atingiu uma performance de **AUC em 0.80**.

---

### Aplicação

Finalizando o projeto, criei uma aplicação web via Streamlit, ligado aos dados e ao modelo preditivo, sendo possível de incluir os parâmetros de satisfação, avaliação, tempo de projeto e tempo na empresa. Assim, é possível de pesquisar a situação de um funcionário especifico e pedir ao modelo para avaliar as chances dele permanecer ou sair da empresa.

![image](https://user-images.githubusercontent.com/14170425/234138444-f613baf6-4d2e-4c4b-9530-ea9d68c67802.png)

---

### Chat GPT

Para levar um pouco mais de informação, aproveitei a onda do momento e fiz a inclusão do ChatGPT no app para realizar uma análise dentro dos parâmetros e trazer insights sobre os resultados obtidos de cada nova pesquisa.

![new print - chat gpt](https://user-images.githubusercontent.com/14170425/234127079-ac9a2d6e-7052-4752-b710-bcf91ec09477.png)

Nesse caso, o pedido para o ChatGPT é feita diretamente na API da OpenAI. Assim, a cada nova consulta, a IA faz uma nova leitura sobre as informações obtidas pelo modelo preditivo e realiza uma nova análise, consequentemente trazendo novos insights.

![2023-04-14_05-40](https://user-images.githubusercontent.com/14170425/234127118-6f2726f8-cf09-4d6a-a67c-9d3f3beadf59.png)

---

### Conclusão

Através desse projeto foi possível praticar e implementar conceitos importantes da Ciência e Engenharia de Dados e propor uma solução para um problema latente e recorrente de qualquer empresa que é a retenção de talentos através da Análise de Dados de Recursos Humanos.

Como um processo de melhoria contínua podemos desenvolver uma automação para executar não só o pipeline de coleta e transformação de dados como automatizar os passo da etapa de Machine Learning e Deploy.
