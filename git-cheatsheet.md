Antes de qualquer interação com o git é necessário identificar seu usuário:

```git
git config --local user.name "Seu nome aqui"
```
	
```git
git config --local user.email "seu@email.aqui"
```

```git
git --version - ver a versão que está instalada
```

```git
git init - Inicializar (criar) um repositório
```
```
git init --bare - Inicializar a pasta em um servidor remoto para receber as alterações
```
```
git status - mostra o status do repositório, arquivos modificados, arquivos não rastreados, etc.
```
```
git add <nomedoarquivo> - para começar a rastrar mudanças nele (adicionando ao repositório)
```
```
git add . - para começar a rastrear mudanças em todos os arquivos da pasta atual
```
```
git rm --cached <nomedoarquivo> - para parar de rastrear mudanças no arquivo, mas o mantem no diretorio
```
```
git rm -f <nomedoarquivo> - para parar de rastrear mudanças no arquivo e o remove do diretório também.
```
```
git commit -m "Mensagem" - para confirmar as alterações no servidor local do git, ele gerará um código de identificação para este commit (ex.: 7bb3fb9) - A mensagem não pode ser vazia
```			 - o primeiro commit no repositório é chamado de "root-commit"


Se um arquivo for modificado, não deve-se apenas dar o commit... o novo arquivo com modificações precisa ser adicionado com o comando git add.

--

HEAD: Estado atual do nosso código, ou seja, onde o Git os colocou
Working tree: Local onde os arquivos realmente estão sendo armazenados e editados
index: Local onde o Git armazena o que será commitado, ou seja, o local entre a working tree e o repositório Git em si.

--
```
git log - mostra o histórico dos commits incluindo o ID, nome e e-mail de quem alterou, branch, e mensagens do commit
```
```
git log --oneline - mostra o histórico dos commits incluindo o ID, nome e e-mail de quem alterou, branch, e mensagens do commit de forma resumida em uma linha
```
```
git log -p - mostra tudo e mais as modificações realizadas nos arquivos.
```


Arquivo: .gitignore
	- Todos as linhas devem conter o nome dos arquivos que o git deve ignorar.
	- para ignorar uma pasta "nomedapasta/"


```
git remote - lista os servidores remotos cadastrados.
```

```
git remote add <nome> <endreço que pode ser URL, pasta na rede, ou pasta)
```

```			       
git remote -v - mostra os servidores e os endereços
```
```			       
git clone  <endereço de um servidor> <opcional:pasta onde será clonada> - copia o repositorio para uma pasta.
```
```
git push <nome do servidor remote> <branch: ex. master> - Envia as alterações do servidor local para o servidor remoto
```
```
git remote rename <nomedorepositorioremoto> <novonomedorepositorioremoto> - Renomear o nome do servidor remoto
```
```
git pull <nomeservidorremoto> <branchremota> - fazer download de uma branch do servidor remoto
```
```
git fetch é o comando que diz para seu repositório local obter informações (meta-dados) no repositório remoto (ele não faz transferência de arquivos, ao contrário do git pull, que além de fazer essa checagem ainda transfere copia para seu repositório local as mudanças que ele encontra no repositório remoto.
```	
	
```
git push -u <servidorremoto <branch local> - enviar a branch local para o remoto, e o -u diz que sempre que der um git push nessa pasta ele enviará para esse remoto
					   - Ou seja, depois desse comando, babsta executar o git push nessa pasta e ele enviará o branchlocal para o servidor remoto definido anteriormente.
```
	
```
git branch <nome> - cria um novo branch

```git branch``` - Listar todas as branches do repositório local


```git branch -a - Listar todas as branches, tanto local como remoto```

	git branch -r - Listar todas as branches no repositório remoto

```
git show-branch - Listar todas as branches com informações de seus commits
```	
git checkout <nome> - passo a trabalhar no branch <nome>

git checkout -b <nome> - cria o branch nome e já começa a trabalhar nele.

git merge <nome> - une, trazendo as alterações da branch <nome> para a branch ativa que está ativa (checkout), mas perde-se o histórico de commit do ramo e cria-se um commit de merge

git rebase <nome> - une, trazendo as alterações da branc <nome para a branch ativa (checkout), colocando os checkouts do master na frente, assim não perde-se o histórico do ramo.

git log --graph - mostra o historico de commits com um grafico de ramos.


git checkout --<nomedoarquivo> - descarta as mudanças de um arquivo que não foi comitada, nem adicionada para comitar
git reset HEAD <nomedoarquivo> - descartar a mudança de um arquivo que não foi comitada, mas foi adicionado para comitar - o arquivo não é removido, ele fica marcado como modificado.

git revert <hash do comit> - desfaz o comit especificado pelo hash

git stash - guarda as modificações não comitadas, para uma área temporária para que a pessoa possa voltar a trabalhar depois - essa modificação ganha um codigo
git stash list - lista todos os códigos de modificações temporárias ainda não comitadas para que a pessoa possa voltar a trabalhar 

git stash apply 0 - valor da stash stash@{0} - 
git stash drop 0 - remove a stash

git stash pop - pega a última modificação adicionada na stash, aplica ela (apply) e depois a remove da stash (drop) ao mesmo tempo.


git checkout <id do commit> - se quiser voltar o status do projeto a um git specifico e ignorar todas as mudanças posteriores.
                              como ele entra em um estado desanexado, as modificaçõe feitas a partir daqui ficarão perdidas.
			      para que não se percam, é necessário Antes criar um branch: git checkout -b novobranch

git diff <id1>..<id2> - mostra as diferenças dos arquivos nas modificações de um commit ate o outro.

git diff - mostra o que foi alterado mas que ainda não foi adicionado para ser comitado.

git tag -a <nomedatag> - adiciona uma tag que marca um estado fixo, utilizado para marcar um release de uma versão.
git tag -a <nomedatag> -m "<mensagem" - adiciona uma tag que marca um estado fixo, utilizado para marcar um release de uma versão, com uma mensagem.

git tag - lista todas as tags disponíveis.

git push <remote> <tag> - envia uma tag (e os arquivos neste status?) - caso isso seja feito, no github é gerado a possibilidade da pessoa fazer download da versão.
                        - mas deve-se lemrar de enviar antes o branch.
                        - Gera uma Release, ou seja, conseguimos baixar um arquivo compactado com o nosso código neste ponto

```
git rebase -i <id> - id do commit anterior aos que eu quero juntar. (o que fica começa por pick, os que vão se unificados marquase com S de Smash)
```

```
git cherry-pick	<id> - pega o comit e copia para a branch em que se está.
```
	
git bisect start - incializa busca para localizar alteração
	git bisect BAD HEAD
	git bisect GOOD <ID de quando estava ruim> Ele então ira buscar entre o HEAD, e o ID.

	ele ira mostrar um commit. caso não seja o bom: git bisect BAD - caso seja o bom: git bisect GOOD

	no momento que encontra: git bisect reset


	git show <ID> mostra as alterações de um commit

```
git blame <nomedoarquivo> - mostra todas as alterações no arquivo para se encontrar o autor de uma alteração 
```
```
git branch -d <titulo> excluir um branch
```

Excluir um branch caso ele tenha alguns commits a frente do master:
```
git branch -D <titulo> 
```

Para treinar: https://git-school.github.io/visualizing-git/#free

Sempre dar um pull antes de trabalhar.

Quando executar um commit: Você nunca deve comitar um código que ainda não funciona.


Branch Master: Onde fica o código de produção, , para onde os trabalhos prontos são enviados.
Branch Desenvolvimento (Develpmente: Onde fica o código em desenvolvimento concluido.
				cria-se para feature para adicionar ou corrigir
				cria-se uma release para testar e depois envia par amastar via merge (adiciona-se a tag de release no master)

hotfix um comcerto urgente em produção, cria-se um branch não se modifica nada em produção e quando concluido da um merge em produção e em desenvolvimento.


Referência: https://devhints.io/git-log


Exemplo de Branches (GitFlow):

development
feature/nome-da-feature
feature/nome-da-feature2
hotfix/v0.1.1
master
release/v0.2.0a
