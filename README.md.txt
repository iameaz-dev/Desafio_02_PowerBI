1. Criei o Banco de Dados "desafio-projeto-iasmim" na Azure;

2. Fiz a integração do Azure com o MySQL Workbench;
	2.1. Tive um erro persistente ao tentar fazer a integração, onde ao testar a conexão retornou o erro: "Failed to Connect to MySQL at desafio-projeto-iasmim.mysql.dat...:3306 with user company. SSL connection error: SSL_CTX_set_default_verify_paths failed". Só consegui realizar a conexão quando apaguei o conteúdo em SSL CA File, deixei em branco e assim o teste de conexão deu certo;
	2.2. Na Azure baixei o arquivo correto para adicionar no campo SSL CA File, adicionei, e ao testar a conexão novamente deu tudo certo;

3. Fiz a criação do database 'azure_company' conforme explicado pela professora e fui criando as tabelas com o script disponibilizado no GitHub da mesma;
	3.1. Percebi um erro no script disponibilizado, onde o código indica a exclusão de uma chave estrangeira denominada "department_ibfk_1" mas essa chave não foi criada previamente. Então procurei nos fóruns e encontrei uma solução, acabei usando esse código corrigido que os colegas disponibilizaram, pois sozinha não consegui corrigir, sendo sincera tive muita dificuldade nessa correção;
	3.2. Deixei esse script corrigido salvo, como também o script com o erro para estudar quando acabar o bootcamp, pois terei mais tempo para praticar e analisar todo o conteúdo estudado;

4. Ao carregar no PowerBI a tabela criada com o MySQL Workbench, notei que duas tabelas constavam como vazias: employee e departament. Mesmo assim abri com o Power Query, pois eu sabia que havia adicionado o conteúdo dessas tabelas com o script MySQL;
	4.1. Ao abrir o arquivo no Power Query, atualizei a visualização em cada uma das tabelas e deu certo, o conteúdo apareceu;

5. Analisei cada uma das tabelas e exclui as colunas que continham valores "Table" e "Value", sempre atenta ao que podia ser ou não importante para o relatório;

6. Modifiquei os tipos de dados das tabelas Departament, Dependent e Employee: onde tinha números e constava como tipo de dado Texto, alterei o tipo de dado para Número Inteiro; 

7. Na tabela Employee o tipo de dado da coluna Salary constava como número decimal, então fiz a alteração para número decimal fixo;

8. Notei que na tabela Employee a linha 5 da coluna Super_ssn estava com valor Null, então fiz a substituição do Null por 888665555, que é o Ssn destinado aos Headquarters, e conforme mandam as instruções do projeto o valor nulo deve ser modificado para gerente;

9. Fiz a mesclagem das tabelas employee e departament tendo employee como base, mesclando como nova consulta e nomeei de 'employee_departament';
	9.1. Reoordenei as colunas para que faça mais sentido na análise;
	9.2. Fiz a exclusão de colunas com dados redundantes;

10. Na nova tabela Employee_Departament notei que algumas colunas eram redundantes, portanto reutilizei para mostrar informações mais pertinentes nessa tabela, e fiz as seguintes alterações na coluna Dno:
	10.1. Nome da coluna Dno mudou para 'Nome_Gerente';
	10.2. Alterei o tipo de dado para Texto;
	10.3. Substitui os valores de 1, 4, 5 para James, Jennifer e Franklin, respectivamente;

11. Fiz a mesclagem das colunas Fname e Lname, utilizando o separador Espaço e nomeei a nova coluna de 'Colaboradores';

12. Exclui as tabelas que ao meu ver não são importantes para o relatório: Sex, Bdate e Adress, pois nessa tabela em específico o que importa é a relação entre Colaboradores, Departamentos e seus respectivos gerentes. As informações detalhadas a respeito de cada colaborador constam na tabela 'azure_company employee';

13. Alterei os nomes das colunas para que façam mais sentido na leitura dos dados;

14. Fiz a mesclagem de consulta como nova das tabelas 'Employee_Departament' e azure_company dept_locations';
	14.1. Exclui as linhas duplicadas;
	14.2. Removi as colunas redundantes;
	14.3. Nomeei a nova tabela de 'Colabs_Dptos';

15. Fiz a mesclagem das colunas que tinham nome do departamento e localização do departamento, com separador personalizado " - " e novo nome 'Dpto_Localidade';
	15.1. Nesse caso a mesclagem das colunas é mais adequada pois as duas encontram-se na mesma tabela e o objetivo é que elas permaneçam nessa tabela, unindo seus dados para que tornem-se únicos;

16. Dupliquei a Colabs_Dptos, fiz o agrupamento dos dados da coluna Gerente afim de contar quantos colaboradores há para cada gerente;
	16.1. Depois fiz a mesclagem da tabela Colabs_Dptos e Colabs_Dptos(2), para que a contagem dos colaboradores sejam incluídos na tabela principal;

17. Nomeei a última tabela criada para 'Dados_Colabs' para que seja a tabela principal para utilizar na criação dos relatórios;

18. Fechei e apliquei as transformações, afim de criar o relatório com base nos dados transformados;

19. Por fim, criei o Relatório de Visão Geral da Empresa 'Azure Company'.
