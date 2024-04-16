# dio-transf-dados
Desafio de Projeto: Coleta e Processamento de dados com Power BI
Nesse repositório também estão, o Power BI e os scripts SQL.

Descrição do desafio módulo 3 – Processamento de Dados Simplificado com Power BI
1.	Criação de uma instância na Azure para MySQL
Tive dificuldade em usar o meu número de telefone para a confirmação da conta. Precisei usar o da minha esposa.

2.	Criar o Banco de dados com base disponível no github
Os scripts foram alterados.
O de criação da base de dados, tinha um erro corrigido conforme abaixo:
alter table departament drop departament_ibfk_1; (Erro)
alter table departament drop foreign key departament_ibfk_1; (Corrigido)
Mesmo assim o script para carregar os dados nas tabelas dava erro e adotei uma sugestão que vi no Forum, para não usar os constraints. Com certeza não é a solução limpa, mas para o objetivo de processar e transformar dados no Power BI entendi ser o suficiente. 

3.	Integração do Power BI com MySQL no Azure
Sem problemas. 

4.	Verificar problemas na base a fim de realizar a transformação dos dados
Os dados de empregados foram carregados em duplicidade, creio resultado das idas e vindas durante a criação do BR. Essa correção foi a primeira transformação necessária. Utilizei a eliminação de linhas.

Diretrizes para transformação dos dados
1.	Verifique os cabeçalhos e tipos de dados
Alterado o valor do salário para decimal fixo.

2.	Modifique os valores monetários para o tipo double preciso
OK

3.	Verifique a existência dos nulos e analise a remoção
Não havia.

4.	Os employees com nulos em Super_ssn podem ser os gerentes. Verifique se há algum colaborador sem gerente
Há apenas um gerente.

5.	Verifique se há algum departamento sem gerente
Não há.

6.	Se houver departamento sem gerente, suponha que você possui os dados e preencha as lacunas.
Não há.

7.	Verifique o número de horas dos projetos
Ok. Não há inconsisitências. Tabela agrupada por projeto e colaborador.

8.	Separar colunas complexas
Separado o endereço na tabela de empregados.

9.	Mesclar consultas employee e departament para criar uma tabela employee com o nome dos departamentos associados aos colaboradores. A mescla terá como base a tabela employee. Fique atento, essa informação influencia no tipo de junção

10.	Neste processo elimine as colunas desnecessárias. 
Ok

11.	Realize a junção dos colaboradores e respectivos nomes dos gerentes . Isso pode ser feito com consulta SQL ou pela mescla de tabelas com Power BI. Caso utilize SQL, especifique no README a query utilizada no processo.
Utilizei a opção MESCLAR do Power Query.

12.	Mescle as colunas de Nome e Sobrenome para ter apenas uma coluna definindo os nomes dos colaboradores
ok


13.	Mescle os nomes de departamentos e localização. Isso fará que cada combinação departamento-local seja único. Isso irá auxiliar na criação do modelo estrela em um módulo futuro.
OK

14.	Explique por que, neste caso supracitado, podemos apenas utilizar o mesclar e não o atribuir. 
Nesse caso, como o objetivo é juntar colunas, a opção Mesclar é a que atende. 

15.	Agrupe os dados a fim de saber quantos colaboradores existem por gerente
Resultado em relatório do Power BI

16.	Elimine as colunas desnecessárias, que não serão usadas no relatório, de cada tabela
Eliminadas

