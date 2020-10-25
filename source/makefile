NOME_PROJETO=rpclista

FLAGS=-ansi

EXEC_CLIENT=client
EXEC_SERVER=server

build: saudacoes generateRPC pipelineCSource

saudacoes:
	@echo "Compilando $(NOME_PROJETO)"

generateRPC: lista.x
	@rpcgen -k $^

pipelineCSource: createExecClient createExecServer

createExecClient: cliente.c lista_clnt.c lista_xdr.c
	@echo "Gerando executável do client"
	@gcc -o $(EXEC_CLIENT) $^ $(FLAGS)

createExecServer: servidor.c lista_svc.c lista_xdr.c
	@echo "Gerando executável do server"
	@gcc -o $(EXEC_SERVER) $^ $(FLAGS)

clean:
	@echo "Limpando"
	@rm -f lista.h lista_* $(EXEC_CLIENT) $(EXEC_SERVER)