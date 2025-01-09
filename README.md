# Projeto-SQL-
Resolução do desafio 03 do curso de analise de dados utilizando linguagem sql para responder as perguntas e criar um dashboard de gerenciamento:

Neste Projeto a ideia era utilizar a linguagem sql para fazer filtros, agrupamento, ordenar e limitar linhas, e assim poder respoder as perguntas do gestor.
cada pergunta preciou de um codigo unico e após criação do melhor tipo gráfico, foi criado um dashboard para que o gestor possa analisar tudo em um só lugar de forma totalmente funcional quais aspectos a empresa precisa melhorar.

a primeira questão levantada foi a seguinte:
01 = Qual a proporção de Generos dos clientes da empresa.
      Select     
      	gender, count (*) as quantidade 
      from leads_basic_details
      group by gender

02 = Qual a média de idade dos clientes:
      Select  
      	round(avg(age),0) as Média_da_idade
      from leads_basic_details

03 = Média de Watched:
      select 
      	language, Avg(watched_percentage) as Media_Porcentagem
      from leads_demo_watched_details
      where watched_percentage > 0.5
      group by language
04 = Quantidade de Leads por Escolaridade:
    select 
    	current_education, count(*) as Quatidade
    from leads_basic_details
    group by current_education
    order by Quatidade

05 = Quantidade de Ligações atendidas
    with ligacoes as
    (    select        lead_id,        call_done_date as data   
     from    leads_interaction_details),
    detalhes as
    (    select         lead_id,        lead_gen_source as origem    
    from    leads_basic_details)
    select     count (detalhes.lead_id),    data,    origemfrom    ligacoesleft join detalhes on ligacoes.lead_id = detalhes.lead_id
    group by origem, data


 

