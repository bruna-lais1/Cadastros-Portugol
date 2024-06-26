# Cadastros-Portugol
Sistema simples de cadastros feito no Portugol Studio, permite cadastrar novo usuário, listar usuários cadastrados, buscar usuários, excluir e sair do sistema.

programa
{
inclua biblioteca Util --> U
inclua biblioteca Texto --> T
inteiro total = 4
inteiro quant, idade[10], n, ponteiro=0, x
caracter opcao
cadeia nome[10], busca, enter, msg, resposta
logico encontrado=falso



	
		funcao inicio()
		{
		limpa()
		escreva("Olá, quantos clientes gostaria de cadastrar? [Máx: ", total, " registros]\n")	
		leia(quant)

		se(quant>0)
		{
		se(quant<=total)
		{
		 menu()
		}
		}
		senao
  		limpa()
  		escreva("Quantidade superior ao limite do vetor, tente novamente\n")
  		U.aguarde(3000)
  		menu()
		}

		funcao menu()
		{
			
		msg = "Menu Geral   |"
		topo()
		
  		escreva("Escolha a opção desejada:\n")
  		escreva("1 - Cadastrar novo usuário\n")
  		escreva("2 - Listar usuários cadastrados\n")
  		escreva("3 - Buscar usuários cadastrados\n")
  		escreva("4 - Excluir usuários cadastrados\n")
  		escreva("5 - Sair do sistema\n")	
  		leia(opcao)
		
		escolha (opcao)
		{
		caso '1':
		{
			cadastro()
		pare
		}
		caso '2':
		{
			listar()
		pare
		}
		caso '3':
		{
			buscar()
		pare
		}
		caso '4':
		{
			excluir()
		pare
		}
		caso '5':
		{
			sair()
		pare
		}
		
		caso contrario:
		{
			limpa()
			escreva("\n\n ATENÇÃO: Opção Inválida!!\n\n")
			Util.aguarde(3000)
			menu()
		pare
		}
		}
		}

		funcao cadastro()
		{
		msg = "Cadastro      |"
		topo()
			
		se(ponteiro < quant)
		
  		{	
  		msg = "Cadastro      |"
  		topo()
  		escreva("Informe o nome do(a) cliente:\n")
  		leia(nome[ponteiro])
  		nome[ponteiro] = T.caixa_alta(nome[ponteiro]) //Altera o nome para caixa alta
  	
  		msg = "Cadastro      |"
  		topo()
  		escreva("Informe a idade que o(a) ", nome[ponteiro], " possui:\n")
  		leia(idade[ponteiro])

		  msg = "Cadastro      |"
  		topo()
  		escreva("AVISO: Cadastro Realizado Com Sucesso!")
  		Util.aguarde(1000)
  		ponteiro++ //mesmo que fazer ponteiro=ponteiro+1
  		limpa()
  		menu()
		}
		
		senao
		{
  		limpa()
  		escreva("AVISO: Limite de Cadastros atingido!")
  		Util.aguarde(3000)	
  		menu()
		}
		}

		funcao listar()
		{
  		limpa()
  		se(ponteiro==0)
		{
			escreva("AVISO: Nenhum registro foi encontrado!\n")
			retornar()
		}
		senao 
		{
			msg = "Lista de Clientes   |"
			topo()

			para(n=0; n<ponteiro; n++)
			{
				escreva("Nome: " , nome[n], " Idade: " , idade[n], "\n")
			}
			retornar()
		}
	
		para(n=0; n<ponteiro; n++)
		{
  		escreva("Lista dos clientes cadastrados\n")
  		escreva("=============================.\n")
  		escreva("Nome: ", nome[ponteiro], " - Idade: ", idade[ponteiro], "\n\n")
  		escreva("=============================.\n")
  		retornar()
		}
		}
	

		funcao buscar()
		{
  		limpa()
  		escreva("Busca de clientes cadastrados\n")
  		escreva("=============================================\n")
  		escreva("Informe o nome do(a) cliente a ser procurado:\n")
  		leia(busca)
  		busca = T.caixa_alta(busca)
  		encontrado=falso

		para(n = 0; n<ponteiro; n++)
		{
		  se(nome[n] == busca)
		{
  		escreva(n+1, " - Nome: ", nome[n], " - Idade: ", idade[n], "\n")
  		encontrado=verdadeiro
		}
		}
			
		se(encontrado==falso)
		{
		  escreva("AVISO: Nenhum cliente foi encontrado com o nome ", busca, ".\n")
		}

		retornar()
		
		}

		funcao retornar()
		{
  		escreva("===========================================\n")
  		escreva("Pressione a tecla [ENTER] para sair\n")
  		leia(enter)
  		menu()
		}

		funcao excluir()
		{
  		limpa()
  		escreva("Exclusão de clientes cadastrados\n")
  		escreva("=============================================\n")
  		escreva("Informe o nome do(a) cliente a ser excluido:\n")
  		leia(busca)
  		busca = T.caixa_alta(busca)
  		encontrado=falso

		para(n = 0; n<ponteiro; n++)
		{
		  se(nome[n] == busca)
		{
  		limpa()
  		escreva("Deseja realmente excluir o usuário ", nome[n], " ? S/N \n")
  		leia(resposta)
  		resposta=T.caixa_alta(resposta)
	
		
		se(resposta=="S" ou resposta=="s")
		{
		  para( x=n; x<ponteiro-1; x++)
		{
			nome[x] = nome[x+1]
			idade[x] = idade[x+1]
			U.aguarde(250)
		}
		
  		encontrado=verdadeiro
  		ponteiro--
  		limpa()
  		escreva("Usuário excluido com sucesso!\n")
		
		}
		senao
		{
			limpa()
			encontrado=verdadeiro
			escreva("O registro do cliente ",nome[n], " foi mantido\n")
			retornar()
		}
		}
		}
		
		}
		funcao sair()
	
		{
  		limpa()
  		escreva("Finalizando o sistema em 05 segundos. . .")
  		Util.aguarde(1000)
  		
  		limpa()
  		escreva("Finalizando o sistema em 04 segundos. . .")
  		Util.aguarde(1000)
  
  		limpa()
  		escreva("Finalizando o sistema em 03 segundos. . .")
  		Util.aguarde(1000)
  
  		limpa()
  		escreva("Finalizando o sistema em 02 segundos. . .")
  		Util.aguarde(1000)
  
  		limpa()
  		escreva("Finalizando o sistema em 01 segundos. . .")
  		Util.aguarde(1000)
  
  		limpa()
  		escreva("Sistema finalizado com sucesso! Obrigada!\n\n\n\n\n\n\n")
		}

		funcao topo()
		{
  		limpa()
  		escreva("====================================\n")
  		escreva("SISTEMA DE CADASTRO - ", msg,"\n")
  		escreva("====================================\n\n")
		}
