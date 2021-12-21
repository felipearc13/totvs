	#PROCESSOS INTEGRAÇÃO TOTVS/TUTOR	

		1. Acadêmico cria a turma e matricula o aluno no TUTOR (sem precisar preencher plano financeiro)
		2. TUTOR envia dados de turmas para o TOTVS (uma vez por turma)
		3. TUTOR envia dados de matricula para o totvs (associando o aluno a turma) 
		4. Financeiro preenche dados financeiros do aluno no TOTVS 
		5. TOTVS envia Plano Financeiro para portal do aluno TUTOR (associando o plano financeiro ao aluno)
		6. Financeiro emite NFS-e para aluno
		7. TOTVS envia NFS-e para portal do aluno TUTOR (associando NFS-e ao aluno)

	#ENVIO DE NOTAS FISCAIS PARA PACIENTES/ALUNOS POR EMAIL

		1. Financeiro emite NFS-e
		2. TOTVS envia NFS-e por e-mail (como TOTVS recebe essa nota da prefeitura? porque tem que usar relatório?)

	#CADASTRO VEM ANTES DA TURMA


	=================================================================================================================
	#DADOS NESCESSÁRIOS

	#PROCESSOS INTEGRAÇÃO TOTVS/TUTOR	

	==================================
	TOTVS
	==================================

		1. Acadêmico cria a turma e matricula o aluno no TUTOR (sem precisar preencher plano financeiro)
	#		1.1 SERÁ UTILIZADA A PRÉ-MATRICULA? SE SIM, COMO FUNCIONA?					
		2. TUTOR envia dados de turmas para o TOTVS (uma vez por turma)
			2.1 CRIAÇÃO DE TURMA (TOTVS)
				2.1.1 EDUCACIONAL > EDUCACIONAL > CURRÍCULO E OFERTA > MATRIZES CURRICULARES > INCLUIR
					Aba identificação:
					- Cód. Curso - ex: 04 DERMATOLOGIA III
					- Cód. Habilitação - ex: 04 DERMATOLOGIA III
					- Código (código da Matriz Curricular) - ex: 11 (Código da Matriz Curricular DERMATOSP2017/III)
					- Matriz Curricular - ex: DERMATOSP2017/III
					- Total de créditos 
					- Carga Horária - ex: 8.640,0000 
					- Data de Início - ex: dd/mm/aaaa
					- Data de Término - ex: dd/mm/aaaa
					- Controle de vagas - ex: por turma
					SALVAR
					2.1.1.1 ANEXOS > PERÍODO > INCLUIR
						Aba identificação
						- Perído - ex: 1
						- Descrição - ex: UNICO
						 2.1.1.1.1 ANEXOS > DISCIPLINAS OPTATIVAS / ELETIVAS > INCLUIR
							- Disciplina #VERIFICAR QUAL DADO É PREENCHIDO EM DISCIPLINA
							SALVAR
					OK
					2.1.1.2 MATRIZ CURRICULAR > ANEXOS > MATRIZ APLICADA > INCLUIR
						- Curso - ex: 04 DERMATOLOGIA III
						#VERIFICAR COM FABRICIO SE DADOS SÃO PREENCHIDOS AUTOMATICAMENTE
						SALVAR
				2.1.2 EDUCACIONAL > EDUCACIONAL > CURRÍCULO E OFERTA > PARAMETRIZAÇÃO POR CURSO > INCLUIR
					Aba identificação
					- Perído letivo - ex: 2017 
					- Curso - ex: 04 DERMATOLOGIA III
					- Conta caixa - ex: 1002 CONTA ITAU ISMD SP #VERIFICAR COM DOUGLAS A DE BH (1001?) 
					2.1.2.1 ANEXOS > DOCUMENTOS EXIGIDOS
					- CÓDIGO - ex: código relativo ao documento #CONFIRMAR COM FABRICIO SE SÃO COLOCADOS UM POR UM - EX: CPF, RG E ETC.
					- QUANTIDADE - ex: quantidade documento #EM QUAL PROCESSO É UTILIZADO NO ACADÊMICO - PERGUNTAR FABRICIO
					2.1.2.1 ANEXOS > MODELO DE ETAPAS DA MATRIZ APLICADA > INCLUIR
					Aba identificação
					- TIPO DE ETAPA - ex: Faltas 
					- CÓDIGO DA ETAPA - ex: 2 FALTAS TOTAIS
					Aba Configuração do modelo de etapa
					- Data de início - ex: dd/mm/aaaa
					- Data de Término - ex: dd/mm/aaaa
					- Fórmula de faltas - ex: Edu.0003 - Cálculo de Faltas Totais
					- Freq. mínima (%) - ex: 75,00
					SALVAR
					2.1.2.2 ANEXOS > MODELO DE ETAPAS DA MATRIZ APLICADA > INCLUIR #VERIFICAR SE ESSE É O CAMINHO CERTO
					Aba identificação
					- Perído letivo - ex: 2017
					- Tipo de etapa - ex: Notas 
					- Código da etapa - ex: 1 PONTOS TOTAIS
					Aba Configuração do modelo de etapa
					- Data de início - ex: dd/mm/aaaa
					- Data de Término - ex: dd/mm/aaaa
					- Fórmula de notas - ex: Edu.0001 - Apuração de resultados
					- Pontos distribuiídos - ex: 100.0000
				2.1.3 EDUCACIONAL > EDUCACIONAL > CURRÍCULO E OFERTA > TURMAS > INCLUIR
					Aba identificação
					- Período letivo - ex: 2016
					- N maximo de alunos - ex: 100
					- Código Turma - ex: DERMATOSP16/III 16 2
					- Data inicial - ex: dd/mm/aaaa
					- Data final - ex: dd/mm/aaaa
					- Nome - ex: DERMATOSP16/III 16 2
					- Prédio - ex: 01 ISMD - SP #VERIFICAR COM FABRICIO QUAL É BH
					- Fórmula para cálculo do resultado final - ex: Edu.0001 - Apuração do resultado final
					Aba Turmas/Disciplinas #ESTÁ EM ANEXOS?
					INCLUIR
					- Turno - ex: INTEGRAL
					- Tipo de Turma - #VERIFICAR OPÇÕES
					- Cod. Disciplina - #VERIFICAR OPÇÕES
					- Data inicial - dd/mm/aaaa
					- Data final - dd/mm/aaaa
					- Prédio - #VERIFICAR SE É EX: 01 ISMD - SP
					- N mínimo de alunos - #TEM LIMITE MINIMO/MÁXIMO?
					- N máximo de alunos - #TEM LIMITE MINIMO/MÁXIMO?


		3. TUTOR envia dados de matricula para o totvs (associando o aluno a turma)
			3.2. MATRÍCULA ALUNO (TOTVS)
				3.2.1. INSCRIÇÃO DE NOVO ALUNO(TOTVS) - EDUCACIONAL > EDUCACIONAL > CURRÍCULO E OFERTA > ALUNOS
					Aba identificação:
					- Código e Registro Acadêmico (preenchido automaticamente no TOTVS)
					- Nome
					- Estado Natal
					- Data de Nascimento dd/mm/aaaa
					- E-mail 
					Aba Endereço
					- CEP
					- Logradouro 
					- Número
					- Bairro 
					- Estado
					Aba Documentos
					- CPF
					- RG (RNE, caso seja estrangeiro)
					Aba Campos Complementares
					- CRM do aluno
					- Senha inicial do Portal (não será nescessária)
				3.2.2 REALIZAÇÃO DA MATRÍCULA DO ALUNO (TOTVS) - EDUCACIONAL > EDUCACIONAL > CURRÍCULO E OFERTA > ALUNO > ANEXOS > CURSOS/HABILITAÇÕES
					- Matriz Aplicada ??????????
					- Situação de Matrícula ????????
					3.2.2.1. ALUNO > PROCESSOS > MATRICULAR ALUNO
						- Período Letivo (ano de inicio do curso)
						- Turma 
						- Situação Atual (cursando)
						- Documentos (conferir se forem entregues)
						- Matérias (selecionar)

		4. Financeiro preenche dados financeiros do aluno no TOTVS 
	#		
		5. TOTVS envia Plano Financeiro para portal do aluno TUTOR (associando o plano financeiro ao aluno)
	#       5.1 VERIFICAR COM DOUGLAS QUAL PLANO FINANCEIRO É ESSE E COMO A TOTVS IRÁ ENVIAR? COMO TUTOR IRÁ DISPONIBLIZAR 
		6. Financeiro emite NFS-e para aluno
	#		6.1 VERIFICAR COM DOUGLAS
		7. TOTVS envia NFS-e para portal do aluno TUTOR (associando NFS-e ao aluno)
	#		7.1 COMO TOTVS IRÁ ENVIAR? VERIFICAR COMO TUTOR PODERÁ DISPONIBILIZAR ISSO
		8. Notificar aluno inadiplente
	#		8.1 COMO O FINANCEIRO CONTROLA A INADIPLÊNCIA? COMO O CONTATO É FEITO HOJE?



	#ENVIO DE NOTAS FISCAIS PARA PACIENTES/ALUNOS POR EMAIL

		1. Financeiro emite NFS-e
			1.1 Movimento 22.00
			1.2 Envia RPS prefeitura
			1.3 Prefeitura retorna (XML? VERIFICAR WEBSERVICE PREFEITURA BH E SP) ?????????????????????
	#	2. TOTVS envia NFS-e por e-mail (como TOTVS recebe essa nota da prefeitura? porque tem que usar relatório?)
			2.1 TOTVS gera relatório com os dados do Cliente/Fornecedor
	#		2.1 TOTVS envia por email ALUNO/CLIENTE(COMO? QUAL PROCESSO)???????????????????