# NEXUS7_Exercicio_Final_v2

DESCRIÇÃO COMPLETA DO QUE SE PEDE:

NEXUS-7  /  GESTÃO DE MISSÃO INTEGRADA 
Relatório de Incidente Técnico — código entregue pela ARIA v0.9.4 
Estruturas de Dados I  /  Ciência da Computação  /  Unipê  /  2026.1 
Prof. Edkallenn Lima 
01  
SITUAÇÃO 
No dia 14 de abril de 2026, a IA de suporte técnico ARIA entregou o código-fonte do sistema de gestão da 
Estação Espacial NEXUS-7. O sistema integra quatro subsistemas: manifesto de tripulação via lista 
encadeada, histórico de missões via pilha, câmara de descompressão via fila estática circular e central de 
suprimentos via deque dinâmico. 
O código compilou. Sem erros de sintaxe. Sem warnings. A ARIA garantiu que estava correto. 
Nos primeiros testes em órbita, quatro subsistemas apresentaram comportamento anômalo. O manifesto 
travou em loop infinito. O airlock aceitou um tripulante além da capacidade declarada. A fila de 
suprimentos perdeu itens silenciosamente após a segunda inserção pelo fundo. O log de missões retornou 
dados de regiões de memória já liberadas. 
A ARIA produz código que compila e parece correto. Os bugs não são de sintaxe. São de lógica, de 
gerência de memória e de estrutura de dados. Eles só aparecem em execução, e alguns só aparecem 
após muitas operações. Este é o tipo de problema que custa vidas em sistemas críticos. 
02  
O QUE ESTÁ EM JOGO 
Este não é um exercício de produção de código. Qualquer IA gera uma implementação limpa desse sistema 
em menos de dois minutos. O ponto não é escrever o código. É entender o que está errado no código que 
foi escrito, e demonstrar esse entendimento por escrito e em tempo real. 
A entrega inclui o código corrigido mais um quiz individual em sala, aplicado na aula seguinte à entrega. O 
quiz referencia diretamente o código que cada aluno submeteu. Quem não rodou o programa e não 
entendeu as correções não consegue responder. Esse é o filtro real do trabalho. 
03  
O CÓDIGO 
O arquivo nexus7_aria.c está disponível junto com este documento. Ele contém a implementação completa 
gerada pela ARIA, com os quatro subsistemas, o TAD Tripulante e um main() de teste. 
Há seis bugs distribuídos pelo código. Nenhum é de sintaxe. O compilador não 
vai ajudar. 
Subsistema 
Estrutura usada pela ARIA 
Manifesto 
Lista encadeada simples (inserção e remoção) 
Histórico 
Pilha dinâmica (empilhar e desempilhar) 
Airlock 
Fila estática circular (capacidade MAX_AIRLOCK = 4) 
Suprimentos 
Deque duplamente encadeado (inserção frente e fundo) 
04  
MISSÃO 
A missão tem duas fases obrigatórias. 
FASE 1  /  AUDITORIA E CORREÇÃO 
Encontre e corrija os seis bugs no arquivo nexus7_aria.c. Não há relatório separado. A compreensão de 
cada correção será verificada no quiz em sala. 
FASE 2  /  EXTENSÃO 
Adicione uma função que não existe no código original. A assinatura esperada: 
float calcularMediaOxigenio(ListaTripulacao* L); 
A função percorre o manifesto completo e retorna a média do campo nivel_oxigenio. Lista vazia retorna 
0.0f com mensagem. Adicione uma chamada no main() com saída formatada em duas casas decimais: 
Média de oxigênio da tripulação: 97.53% 
05  
ENTREGA 
Arquivo 
ED-lista2-nexus7-SeuNome.c 
Conteúdo 
Código corrigido + calcularMediaOxigenio + cabeçalho padrão 
Via 
Blackboard (upload) ou link GitHub/Repl 
Prazo 
Conforme data publicada no Blackboard 
O repositório GitHub não pode ser um clone de outro. Repositórios idênticos ou clonados resultam 
em anulação automática do trabalho. 
06  
QUIZ INDIVIDUAL EM SALA 
Na aula seguinte à entrega, cada aluno responde individualmente a um quiz de 25 minutos via Blackboard, 
sem acesso à internet. O arquivo .c submetido ficará disponível para consulta durante o quiz. As questões 
referenciam diretamente o código corrigido e a função calcularMediaOxigenio implementada. 
O quiz tem oito questões: seis de múltipla escolha ou verdadeiro/falso, corrigidas automaticamente, e duas 
dissertativas curtas, corrigidas manualmente. 
Quem não rodou o código não consegue responder às questões 7 e 8. Quem não entendeu as correções 
não acerta as questões 1 a 6. O quiz não pode ser preparado memorizando respostas genéricas. 
07  
BANCO DE QUESTÕES DO QUIZ 
As questões abaixo são exatamente as que compõem o quiz do Blackboard. Não há surpresa de conteúdo. 
A diferença entre quem estudou e quem não estudou aparece no tempo disponível: 25 minutos é suficiente 
para quem entende, insuficiente para quem vai tentar descobrir na hora. 
QUESTÕES 1 A 6  /  múltipla escolha e verdadeiro/falso 
01)  A função inserirTripulante foi implementada com um erro. Qual instrução está faltando após a linha novo
>prox = L->cabeca? 
Opções: (a) L->cabeca = novo;  (b) novo->prox = NULL;  (c) L->tamanho = 0;  (d) free(novo); 
02)  A função imprimirManifesto entra em loop infinito com qualquer lista não vazia. Qual instrução está 
ausente dentro do bloco while? 
Opções: (a) atual = atual->prox;  (b) atual = atual->ant;  (c) L->cabeca = atual;  (d) atual = NULL; 
03)  Qual tipo de erro ocorre em desempilharMissao quando ela retorna a variável resultado após o 
free(temp)? 
Opções: (a) Use-after-free  (b) Memory leak  (c) Null pointer dereference  (d) Buffer overflow 
04)  O airlock tem MAX_AIRLOCK igual a 4. Quantas chamadas a enfileirarAirlock têm sucesso antes de recusar 
uma inserção? 
Opções: (a) 3  (b) 4  (c) 5  (d) 2 
05)  Verdadeiro ou falso: a ausência de free(atual) em removerTripulante causa memory leak — o nó 
removido permanece alocado no heap sem nenhum ponteiro referenciando-o. 
06)  Em inserirFundoDeque, o que está ausente para que inserções sucessivas pelo fundo funcionem 
corretamente? 
Opções: (a) Atualizar D->cauda = novo e, se lista vazia, D->frente = novo  (b) Definir novo->prox = NULL  (c) 
Decrementar D->tamanho  (d) Liberar o nó anterior 
QUESTÕES 7 E 8  /  dissertativas curtas (máximo 5 linhas cada) 
07)  Descreva o que acontece operacionalmente quando o bug de enfileirarAirlock é ativado com 
MAX_AIRLOCK = 4. Por que isso é crítico em uma câmara de descompressão espacial? 
Referência esperada: quinto tripulante aceito, posição sobrescrita, risco de falha de vedação. 
08)  Usando os três tripulantes do main() (nivel_oxigenio: 98.5, 95.0 e 99.1), calcule manualmente o valor 
retornado por calcularMediaOxigenio. Mostre a conta e o formato de saída esperado. 
Referência: (98.5 + 95.0 + 99.1) / 3 = 292.6 / 3 = 97.53. Saída: Média de oxigênio da tripulação: 97.53% 
08  
AVALIAÇÃO 
Seis bugs corrigidos 
35% 
calcularMediaOxigenio 
15% 
Cabeçalho e 
nomenclatura 
10% 
Quiz individual em 
sala 
40% 
Um único arquivo. O quiz em sala verifica a compreensão. Não há relatório separado para escrever 
nem para corrigir. 
Bom trabalho. 




update 1.0
O que foi feito até o momento:

1)
