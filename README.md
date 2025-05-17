# AI_Chef
Projeto Imersão IA 3ª Edição Alura + Google Gemini
Este projeto implementa um sistema de agentes de IA para auxiliar na busca, seleção e análise de receitas culinárias. Ele utiliza o modelo Gemini do Google, o framework de agentes do Google (Google ADK) e a API do Google Sheets para fornecer um assistente de cozinha inteligente.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Visão Geral
O sistema de agentes foi projetado para guiar o usuário desde a entrada dos ingredientes disponíveis até a apresentação de receitas detalhadas, incluindo informações nutricionais e até a criação de gráficos comparativos no Google Sheets.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Os principais agentes são:

Agente Buscador: Responsável por pesquisar receitas na web (Google e YouTube) com base nos ingredientes fornecidos pelo usuário.
Agente Gastronômico: Filtra e seleciona as melhores receitas, fornecendo detalhes como ingredientes e modo de preparo.
Agente Nutricionista: Avalia as receitas selecionadas do ponto de vista nutricional, sugere ajustes para torná-las mais saudáveis e gera uma planilha no Google Sheets com a análise nutricional.
Agente Redator: Formata as receitas finais em um estilo de revista gastronômica, incluindo tabelas nutricionais e gráficos comparativos.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Funcionalidades
Pesquisa de receitas baseada em ingredientes fornecidos pelo usuário.
Seleção e detalhamento das melhores receitas.
Análise nutricional das receitas.
Sugestões para tornar as receitas mais saudáveis.
Geração de planilhas do Google Sheets com dados nutricionais e gráficos comparativos.
Apresentação das receitas em formato de revista gastronômica.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Pré-requisitos
Antes de executar o código, você precisará configurar o seguinte:

Google API Key: Obtenha uma API Key do Google e configure a variável de ambiente GOOGLE_API_KEY.

Google Sheets Credentials: Você precisará de um arquivo de credenciais de conta de serviço do Google Cloud Platform para acessar o Google Sheets. Configure a variável de ambiente GOOGLE_SHEETS_CREDENTIALS com o conteúdo deste arquivo JSON (é recomendado usar o Google Colab userdata para armazenar isso de forma segura).

Bibliotecas Python: Instale as bibliotecas necessárias usando o seguinte comando:

Bash

pip install google-genai google-adk gspread google-auth

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Configuração
API Key do Google Gemini:

Obtenha sua API Key do Google Gemini.

No Google Colab, você pode usar o userdata.get() para armazenar e acessar sua chave de forma segura:

Python

import os
from google.colab import userdata

os.environ["GOOGLE_API_KEY"] = userdata.get('GOOGLE_API_KEY')
Credenciais do Google Sheets:

Crie um projeto no Google Cloud Platform e habilite a API do Google Sheets e a API do Google Drive.

Crie uma conta de serviço e gere um arquivo de credenciais JSON.

Armazene o conteúdo desse arquivo JSON no Google Colab userdata sob a chave GOOGLE_SHEETS_CREDENTIALS:

Python

import os
from google.colab import userdata
import json

os.environ["GOOGLE_SHEETS_CREDENTIALS"] = userdata.get('GOOGLE_SHEETS_CREDENTIALS')
Certifique-se de que a conta de serviço tenha permissão para acessar suas planilhas do Google Sheets.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Como Usar
Execute o script Python no Google Colab ou em um ambiente Python com as dependências instaladas e as variáveis de ambiente configuradas.
O script solicitará que você insira os ingredientes que você tem disponíveis.
O sistema de agentes processará sua solicitação e fornecerá as receitas conforme descrito nas funcionalidades.
Exemplo de Uso
❓ Por favor, digite quais ingrediente você possui para cozinhar: frango, batata, cebola
O sistema irá então pesquisar, selecionar, analisar e formatar receitas utilizando esses ingredientes.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Estrutura do Código
O código é organizado em funções e classes que representam os diferentes agentes e ferramentas:

agente_buscador(): Função que define e executa o agente buscador.
agente_gastronomico(): Função que define e executa o agente gastronômico.
agente_nutricionista(): Função que define e executa o agente nutricionista, incluindo a interação com o Google Sheets.
agente_redator(): Função que define e executa o agente redator, formatando as receitas e criando gráficos.
GoogleSheetsTool: Classe que encapsula as funcionalidades de interação com o Google Sheets (criar planilhas, escrever dados e criar gráficos).
Funções auxiliares como call_agent() (para executar os agentes) e to_markdown() (para formatar a saída).
Modelos de dados (usando Pydantic) para definir a entrada das funções do Google Sheets.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Observações
O código utiliza o Google Colab userdata para armazenar credenciais de forma segura. Se você estiver executando o código em outro ambiente, precisará adaptar a forma de carregar as credenciais.
A criação de gráficos no Google Sheets é realizada através da construção de solicitações para a API do Google Sheets, o que pode ser complexo. O código fornece um exemplo básico de gráfico de linhas.
O sistema de agentes pode ser estendido para incluir mais funcionalidades ou integrar outras APIs.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Contribuição
Contribuições para melhorar este projeto são bem-vindas. Sinta-se à vontade para enviar pull requests ou abrir issues no repositório.
