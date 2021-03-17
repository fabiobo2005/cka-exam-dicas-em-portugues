# Certificação CKA - Dicas em Pt-Br
Repositório com dicas para o exame CKA da Linux Foundation.

Recentemente consegui passar na prova de certificação [CKA da Linux Foundation](https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/). Realmente foi um desafio, além de ser uma prova com bastante conteúdo, você tem que provar na prática seus conhecimentos. 
Na Prática Mesmo!!!
A prova é composta por vários desafios que você precisa cumprir em 2h utilizando um ambiente real com um terminal e alguns clusters de K8S. No site oficial do exame tem um descritivo do ambiente, mas vou colocar aqui para vocês terem uma ideia de como é o ambiente.


Ambiente da Prova: [informações importantes](https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad)

 [--- CKA Exam Clusters ---](https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad#cka-and-ckad-environment)

| Cluster | Membros | CNI | Descrição |
|---------|---------|-----|-----------|
| k8s     | 1 master, 2 workers | flannel | k8s cluster |
| hk8s    | 1 master, 2 workers | calico  | k8s cluster |
| bk8s    | 1 master, 1 workers | flannel | k8s cluster |
| wk8s    | 1 master, 2 workers | flannel | k8s cluster |
| ek8s    | 1 master, 2 workers | flannel | k8s cluster |
| ik8s    | 1 master, 1 base node | loopback | k8s cluster − missing worker node

Além dos cluster da tabela acima, você irá usar uma estação (terminal) que dará acesso a todos os cluster, e é de lá que você irá efetuar a maior parte do trabalho.

E como foi minha preparação. Li muitos documentos no [site oficial](https://kubernetes.io/docs/home/) e também vários blogs que se referem ao exame. Vou deixar uma lista de links e blogs de referência no final.

Para estudar e ganhar mais conhecimento eu fiz a assinatura do portal [KodeKloud](https://kodekloud.com/) no plano anual por USD 19/m que com a conversão atual ficam R$1300 mais ou menos. Nossa muito dinheiro alguns vão dizer, porém além de acesso ao curso do CKA dentro do portal existe toda uma trilha de aprendizado para quem quer se especializar em Kubernetes e DevOps com treinamentos de Kubernetes, Docker, Git, Linux, Terraform, Ansible, OpenShift e outros, então na minha opinião vale cada centavo, mas se você está em um momento de grana curta o treinamento de CKA está disponível no [Udemy](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/) e muitas vezes conseguimos encontrar descontos de até 93% (hoje 15/03/2021 o preço é R$22.90, já o preço original R$349.90. Economia de 93% off).
Nos dois treinamentos existem laboratórios que vão te ajudar a conhecer o Kubernetes e tudo que é necessário para não só passar no exame de certificação, mas poder trabalhar como administrador de ambiente K8S.
Antes da prova eu também comprei o simulado [Killer.sh](https://killer.sh), este simulado é muito mais difícil que a prova e possui todos os exercícios e tarefas necessárias que você precisa dominar para passar no exame.

Minha rotina foi de estudar todos os dias, inclusive sabados e domingos por pelo menos 3h, então de segunda a sexta eu começava a estudar as 19:00hs e terminava as 22:00hs e aos finais de semana eu aproveitava que sempre me levanto muito cedo e começava a estudar as 08:00hs até 11:30hs e depois só retornava as 15:00hs até 19:00hs, parece muito puxado, mas na verdade com a situação de pandemia que estamos vivendo e sem sair de casa eu aproveitei o momento para dedicar aos estudos e não ficar vendo séries na Netflix ou jogando VG 😅. Importante também é entender e respeitar seus limites, muitas vezes me senti muito cansado ou até exausto ao final de um dia longo de trabalho, portanto nestes momento eu me dei o devido descanço, tomei uma IPA e coloquei algumas séries em dia.

Ok chega de enrolação e vamos as dicas

## Dica 01 - Tenha sempre em mãos uma K8S para chamar de seu.
Faça instalação local em seu computador pessoal ou de trabalho, o importante aqui é não precisar de uma infraestrutura complexa para treinar alguns comandos quando você tiver um tempo livre. Por facilidade e pelo fato de já ter trabalhado com Docker-Desktop antes foi o que utilizei no meu laboratório local, porém recomendo vocês a testarem as opções e utilizar a que achar mais fácil e simples para você. 

Algumas opções:
- [Docker Desktop](https://www.docker.com/products/kubernetes)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [Canonical MicroK8s](https://microk8s.io/docs)
- [Kind](https://kind.sigs.k8s.io/)
- [Play with Kubernetes](https://labs.play-with-k8s.com/) -- O **"Play with Kubernetes"** é uma plataforma online e free que você pode utilizar também.

## Dica 02 - Documentação do K8S. Livre para usar!
Faça utilização da documentação, tudo que você precisa saber sobre K8S está na documentação. E você pode utilizar durante a prova, isso mesmo... 🤯 é permitido colar (copy&paste) da documentação oficial para te ajudar durante o exame, mas fique atento somente a seguinte lista de sites são permitidos durante o exame:

- https://kubernetes.io/docs/, 
- https://github.com/kubernetes/, 
- https://kubernetes.io/blog/

E nenhum outro domínio/site é permitido, inclusive o https://discuss.kubernetes.io/.

No [GitHub do Piotr](https://gist.github.com/Piotr1215/016ba7218a1a949574786fb9b92382c1) tem uma lista de links que você pode salvar nos seus favoritos e usar como referência durante a prova para agilizar a busca por determinados assuntos. Eu fiz algumas modificações e adicionei alguns links no meu próprio arquivo de favoritos e vou deixar aqui para vocês decidirem qual preferem utilizar.

## Dica 03 - Conheça os atalhos do editor de texto
Durante a prova você vai precisar usar muito editor de texto, muitas tarefas exigem que você crie e modifique arquivos YAML e você vai precisar saber utilizar um editor de texto e conhecer seus atalhos pode ser um grande aliado. O mais utilizado é o "vi" (vim), já li em alguns blogs que usam outros editores como "nano", mas eu utilizo o "vi" e recomendo. Alguns links para ajudar:
- [Vim Cheat Sheet](https://vim.rtorr.com/lang/pt_br)
- [Wikipedia Vi Editor](https://en.wikipedia.org/wiki/Vi)
- [GitHub Vim](https://github.com/vim/vim)

Eu já disse que você vai precisar editar muito texto! Bem não custa nada avisar.

## Dica 04 - Crie atalhos e economize seu tempo
Criar apelidos (alias) e variáveis no seu terminal irá te salvar um enorme tempo e economizar alguma digitação, e é claro diminuir a chance de algum "typo" erro.
Além disso o kubectl (dica sobre kubectl mais a frente) permite você configurar a função de autocompletar que na prática ajuda muito para finalizar de maneira mais rápida comandos no terminal.
Veja detalhes em: [Kubectl autocomplete](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#kubectl-autocomplete)

Minha lista:
```
#Alias
#CONFIG_ALIAS_N_COMPLETION
source <(kubectl completion bash)
echo "source <(kubectl completion bash)" >> ~/.bashrc
complete -F __start_kubectl k
alias k=kubectl
alias kgp="kubectl get pods"
alias kgs="kubectl get service"
alias kd="kubectl delete"
alias kcf="kubectl create -f"
alias kaf="kubectl apply -f"
alias kgpa="kubectl get pods -A"
alias kg='kubectl get'
alias ke='kubectl explain'
alias cls=clear
alias reload="systemctl daemon-reload"
alias cluster='kubectl cluster-info'
alias ctx=kubectx
alias ns=kubens
alias kube-cert="cd /etc/kubernetes/pki"
alias etcd-cert="cd /etc/kubernetes/pki/etcd"
alias manifest="cd /etc/kubernetes/manifests"
export PATH=~/.kubectx:$PATH
export do="-o yaml --dry-run=client"
export sys="-n kube-system"
export ETCDCTL_API=3
```

## Dica 05 - Kubectl Modo Imperativo
Existe um [blog](https://medium.com/faun/be-fast-with-kubectl-1-18-ckad-cka-31be00acc443) só para ajudar em como se tornar "rápido" ao utilizar o kubectl. Em meu treinamento percebi que se tornar "rápido" com **kubectl** é só questão de tempo e familiaridade, pois quanto mais você treina, mais você conhece a ferramenta e mais rápido consegue executar tarefas. 

Muitas tarefas podem ser finalizadas de maneira imperativa, ou seja, somente usando o comando kubectl , porém vão existir tarefas que você começa com o modo imperativo e precisa terminar com o modo declarativo, quer dizer que você vai executar um comando que pode gerar um documento/manifesto tipo Json ou YAML (preferencialmente YAML) e aplicar as modificações solicitadas na tarefa.

Mas claro vou deixar aqui alguns exemplos de utilização do modo imperativo que podem economizar o seu tempo.

```
#POD Command Sleep
kubectl run busybox --image=busybox --restart=Never --/bin/sh -c "sleep 3600"
kubectl --namespace=NAME_SPACE run --restart=Never busybox --image=busybox -- sleep 1d

#Kubectl run with lots of options
kubectl run busybox --image=busybox --requests='cpu=100m,memory=256Mi' --restart=Never --serviceaccount=admin --record=true --save-config=true --labels='key:value,app:busybox,tier=frontend'--env="key=value" -o yaml --dry-run=client -- /bin/sh -c "sleep 3600" > busybox.yaml

#POD DNSUtils
kubectl apply -f https://k8s.io/examples/admin/dns/dnsutils.yaml

#POD runs command "env" save output to a file
Kubectl run busybox --image=busybox --restart=Never --rm -it -- env >>envpod.txt
#--rm=false: If true, delete resources created in this command for attached containers.

#POD Says "Hello world" and exists
kubectl run busyboxy --image=busybox -it --rm --restart=Never --/bin/sh -c 'echo hello world'
kubectl get pods --> No pod busybox running

#POD with port
kubectl run nginx --image=nginx:1.17.4 --restart=Never --port=80 --labels=app=nginx

# Secrets
kubectl create secret generic super-secrect --from-literal=username=alice --from-literal=password='alice'

#JSONPATH Example
kubectl get deployments.apps -o jsonpath='{.metadata.name}{.spec.template.spec.containers[].image}{.items.spec.replicas}{.metadata.namespace} --sort-by=.metadata.name

#CUSTOM-COLUMNS
kubectl get deployments.apps -o custom-columns='DEPLOYMENT:.metadata.name, CONTAINER_IMAGE:.spec.template.spec.containers[].image, READY_REPLICAS:.spec.replicas, NAMESPACE:.metadata.namespace' --sort-by=.metadata.name

#Jsonpath sort pods created timestamp
#List all the pods sorted by created timestamp
kubectl get pods -A --sort-by=.metadata.creationTimestamp

#Jsonpath List Pods name and namespace
#List all the pods showing name and namespace with a json path expression
kubectl get pods -A -o=jsonpath="{.items[*]['metadata.name','metadata.namespace']}"

#Jsonpath POD Name and Start time
kubectl get pods -o jsonpath='{range.items[*]}{.metadata.name}{"\t"}{.status.podIP}{"\n"}{end}'

#Sort pod by label cpu-utilization
#kubectl top pod -l name=cpu-utilizer > /opt/cpu-utilizer.txt

#Add Annotate to a POD/Deploy/DaemonSet
kubectl annotate pod <pod_name> name=webapp
kubectl describe pod <pod_name> | grep -i annotations

#Update all pods in the namespace
#kubectl annotate pods --all description='my frontend running nginx'

#Kubectl Logs 
#Extract logs from Pods
kubectl logs <pod_name> | grep <specific_word>
#Word example: Extract log lines corresponding to error unable-to-access-website
Kubectl logs <pod_name> | grep unable-to-access-website >> /opt/foo
#Kubectl Logs -- write logs to file
kubectl logs frontend | grep -i "unable" > /opt/error-logs

#Check logs from multi-pod 
#kubectl logs <pod_name> -c <container-name>

#List PV by storage capacity
#kubectl get pv --sort-by=.spec.capacity.storage >> /opt/volume_list

#Undo deployment image version (previous / newer)
kubectl rollout undo deploy <name_of_deploy> --record
kubectl describe deploy <name_of_deploy> | grep -i Image

#List pods with different levels of verbosity
kubectl run nginx --image=nginx --restart=Never --port=80
kubectl get pod nginx --v=7
kubectl get pod nginx --v=8
kubectl get pod nginx --v=9

#POD/Deployment & Services Type NodePort
kubectl run nginx --image=nginx --restart=Never --labels=app=my-nginx --port=80 $do >>nginx.pod.yaml
kubectl expose pod nginx --name=<service_name> --type=NodePort --port=80 --namespace=<default> $do >nginx-pod-service.yaml
vi nginx-pod-service.yaml

```
Alguns dos comandos acima utilizei durante o exame e alguns até mais de uma vez. Veja mais exemplos no arquivo cka-dicas.txt, assim como exemplos de manifestos YAML que podem ajudar também durante seu exame.

## Dica 06 - Gerenciamento de tempo
A prova é 100% "hands-on" com até 20 questões e cada questão tem um peso (porcentagem diferente) e com duas (2) horas de duração, isso dá aprox. 6 minutos para resolver cada tarefa, ou seja, gerenciamento de tempo é tão importante quanto dominar o **shell**.

Como todas as questões tem pesos diferentes, não invista seu tempo em um desafio complexo com um peso igual ou menor que %4, marque a questão e vá resolver as questões com maior, ao final do exame você terá tempo suficiente para ir resolver as questões de menor peso, mas agora com mais tranquilidade pois as com maior representação na sua nota já foram resolvidas.

Não fique nervoso e nem se sinta preso em uma questão com peso maior, marque a questão e vá executar a próxima. Quando for fazer a revisão você vai investir tempo para resolver a tarefa e ler a documentação oficial.

## Dica 07 - Fique calmo - \o/ cka tem segunda chance grátis
Fique calmo, você se preparou para o exame, treinou muitas e muitas vezes, portanto fique calmo 😉
O exame possui uma nova tentativa em caso de falha gratuitamente, o que pode se tornar uma vantagem (meu caso), pois agora você conhece na pratica como é o exame, quais tipos de perguntas e vai conseguir controlar melhor o tempo em sua segunda tentativa, caso seja necessário.

## Dica bônus
O ambiente do exame possui um terminal onde não funciona o Ctrl+C & Crtl+V, porém se você assim como eu utiliza o Windows, pode usar os atalhos: Ctrl+Insert para copiar e Shift+Insert para colar. (para outros sistemas operacionais ver no site: https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad para maiores informações). 

Calma isso ainda não é a dica bônus, mas uma introdução para o que você pode fazer agora que sabe como usar o atalho Shift+Insert. 

O Windows 10 possui um tool chamado Clipboard que você pode usar com o atalho **"Windows logo key  + V"** uma vez que o "Clipboard tool" aparecer você pode fixar (usar um pin) em um determinado texto no histórico da área de transferência e utilizar/acessar este texto a qualquer momento apenas acionando o atalho "Windows logo key+V" e com isso não precisar decorar alguns comandos ou usar para suas variáveis como exemplo: "-o yaml --dry-run=client" onde você fixa este texto e depois vai somente acessando do seu histórico a qualquer momento.


## Links & Referências:
| Nome | Autor |
|------|-------| 
| [Preparation and resources for CKA exam](https://medium.com/faun/preparation-and-resources-for-cka-exam-ca868fc678c9) | [Piotr](https://piotrzan.medium.com/) |
| [Kubernetes-Certified-Administrator](https://github.com/walidshaari/Kubernetes-Certified-Administrator) | [Waldi Shaari](https://github.com/walidshaari) |
| [How I passed the CKA Exam](https://medium.com/@amgill1234/how-i-cleared-99-on-cka-exam-9b56cc76bf5b) | [Amrit Gill](https://medium.com/@amgill1234) | 
| [Be fast with Kubectl 1.19 CKAD/CKA](https://medium.com/faun/be-fast-with-kubectl-1-18-ckad-cka-31be00acc443) | [Kim Wuestkamp](https://wuestkamp.medium.com/) |
| [How to ace the Certified Kubernetes Administrator (CKA) exam](https://medium.com/faun/how-to-ace-the-cka-certified-kubernetes-administrator-exam-67dca7f71cfe) | [Sch Shmuel](https://sch-shmuel.medium.com/)
| [Kubernetes the Hard Way](https://github.com/mmumshad/kubernetes-the-hard-way) | [Mumshad Mannambeth](https://github.com/mmumshad)


