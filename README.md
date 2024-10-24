# Prova de Avaliação de Conhecimentos em PHP

**Nome:** Bruno Henrique de França Oliveira  
**Data:** 24/10/2024  
**Tempo de duração:** 1h30min

## Questões

### 1) Qual variável global contém a informação sobre cabeçalhos, paths e localização dos scripts? (Nível fácil)

a) $_SESSION  
b) $_GLOBALS  
c) $_SERVER  
d) $_GET  

**Resposta:** c) `$_SERVER`

### 2) Como você cria um array em PHP? (Nível fácil)

a) $cars = "Volvo", "BMW", "Toyota";  
b) $cars = array["Volvo", "BMW", "Toyota"];  
c) $cars = array("Volvo", "BMW", "Toyota");  

**Resposta:** c) `$cars = array("Volvo", "BMW", "Toyota");`

### 3) Assumir que o seu arquivo index.php está no diretório: `c:/apache/htdocs/phptutor/index.php`. Se você usar o comando `$_SERVER['PHP_SELF']` na sua página index.php, qual será o retorno dessa função? (Nível médio)

a) phptutor/index.php  
b) /phptutor/index.php  
c) c:/apache/htdocs/phptutor/index.php  
d) index.php  

**Resposta:** b) `/phptutor/index.php`

### 4) Construtor pai não é chamado ___________________ se a classe filha define um construtor. (Nível médio)

a) implicitly  
b) explicitly  

**Resposta:** a) implicity

### 5) Qual é a saída do código abaixo? (Nível fácil)

```php
<?php
$father = "mother";
$mother = "son";
echo $$father;
?>
```

a) son  
b) mother  
c) motherson  
d) error  

**Resposta:** a) son

### 6) Por que o comando a seguir não é seguro? include($_GET["file"].".php"); (Nível médio)

a) Haverá um erro fatal se o arquivo especificado não existir.  
b) Haverá um erro fatal se o arquivo “file” não estiver definido no array $_GET.  
c) Um hacker pode fazer um upload de um arquivo PHP usando este comando.  
d) Um hacker pode explorar uma vulnerabilidade neste site através da inclusão de arquivos quenão estão no document root.

**Resposta:** d) Um hacker pode explorar uma vulnerabilidade neste site através da inclusão de arquivos que
não estão no document root.

### 7) Qual das opções abaixo melhor descreve o mecanismo de serialização? (Nível fácil)

a) Serialização permite que quase todos os tipos de variáveis possam ser armazenadas como string, mesmo arrays e objetos.  
b) Serialização é um fácil mecanismo que permite que os desenvolvedores consigam gerar números seriais dentro do código.  
c) Serialization allows developers to use the serial and USB ports of the server.  
d) Serialization creates multiple chains of objects based on integer values.

**Resposta:** a) Serialização permite que quase todos os tipos de variáveis possam ser armazenadas como
string, mesmo arrays e objetos.

### 8) Considere uma classe PHP de data, implemente um método/função “advance”, que devolve o próximo dia, garantindo que todos os membros da classe sejam atualizados devidamente (dia, mês, ano):

**Resposta:**
```php
<?php

class Data
{
    private DateTime $date;

    public function __construct(int $day, int $month, int $year)
    {
        $this->date = new DateTime();
        $this->date->setDate($year, $month, $day);
    }

    /**
     * Avança a data em um dia.
     *
     * @return void
     */
    public function advance(): void
    {
        $this->date->modify('+1 day');
    }

    /**
     * Retorna a data formatada como DD/MM/AAAA.
     *
     * @return string
     */
    public function display(): string
    {
        return $this->date->format('d/m/Y');
    }
}

$data = new Data(31, 12, 2023);
echo "Data atual: " . $data->display() . PHP_EOL;

$data->advance();
echo "Próximo dia: " . $data->display() . PHP_EOL;
```

### 9) O meu chefe quer montar um site de e-commerce para a loja de sapatos (adultos) da esposa dele. Ele escutou que a melhor tecnologia é PHP com PostgreSQL. Posto isto, descreva:

a. Qual sistema operacional você escolheria? Por que?

**Resposta:** Eu escolheria Linux, provavelmente Ubuntu Server, porque é seguro, estável e tem suporte excelente para PHP e PostgreSQL. Além disso, é amplamente usado em servidores.

b. Qual versão do PHP você daria como sugestão? Por que?

**Resposta:** Sugiro usar o PHP 8.3. Por ser a versão mais recente e estável, conta com várias melhorias de desempenho, como JIT (Just-In-Time compiler) e outras otimizações internas, correções de vulnerabilidades, além do suporte a recursos modernos como enums, atributos, propriedades promovidas e suporte a tipagem forte.

c. Qual biblioteca é necessária para você montar PHP conversando com PostgreSQL?

**Resposta:** Usaria PDO com o driver pdo_pgsql. Ele permite fazer consultas seguras com prepared statements, ajudando a proteger contra SQL injection.

d. Defenda o uso de PostgreSQL em relação ao MySQL

**Reposta:** PostgreSQL é ótimo para dados mais complexos, como arrays e JSON, além de ser mais aderente aos padrões SQL. Ele também lida melhor com transações e tem controle de concorrência mais avançado.

e. Qual framework você sugere para uso? Por que?

**Resposta:** Eu sugiro Laravel, porque facilita o desenvolvimento, já vem com várias implementações nativas de segurança (como CSRF e proteção contra SQL injection), tem uma comunidade grande e ativa, está em constante melhoria e tem muito material de suporte, além da documentação.

#### O meu chefe tem um contrato com o PagSeguro (meio de pagamento) e falou que vai usar essemesmo contrato com a loja da esposa.

f. Como você faria a integração com o PagSeguro? Explique ou monte um diagrama da
comunicação entre a loja e o PagSeguro?

**Resposta:** A integração com o PagSeguro seria feita usando a API REST deles. Quando o cliente finaliza a compra, mandamos os dados para o PagSeguro, ele processa o pagamento e devolve o status (aprovado, recusado, etc). Também configuraríamos um webhook para que o PagSeguro nos avise sobre mudanças no status dos pagamentos.
```text
Cliente ---> [Frontend - Finailza o carrinho] ---> [Backend - Cria o pedido e envia para o PagSeguro] ---> [PagSeguro API - Cria e processa o pagamento]
                                                                        |                                                          |
                                                                        |<---------------------[Status de pagamento]---------------|
                                                                    (Webhook notifica o status do pagamento ao backend quando há mudanças)
```

#### Ele também escutou que esse negocio de e-commerce tem riscos de segurança.

g. O que você sugere como segurança? A sua resposta será avaliada pela completude

**Resposta:**  
Para segurança, eu garantiria:  
*SSL para criptografia.*  
*Prepared statements para proteger contra SQL injection.*  
*Proteção CSRF em formulários.*  
*Validação e sanitização de dados de entrada.*  
*Autenticação forte (usando bcrypt ou argon2).*  
*Monitoramento com logs e backups automáticos.*  

### 10) Tenho o código abaixo, comente quais melhorias você faria e porquê.

```php
echo '<h1>New Users</h1>';
$sql = "SELECT * FROM users ORDER BY date_registered";
$result = mysql_query($sql) or die(mysql_error());
echo '<table class="my-table-class">';
while($row = mysql_fetch_assoc($result)) {
  echo '<tr><td>' . $row['username'] . '</td><td>' . $row['date_registered'] . '</td></tr>';
}
echo '</table>';
function random_custom_function($var) {
  $var = $var + 1;
  return '<span style="font-weight:bold;">' . $var . '</span>';
}
$sql = "SELECT * FROM table WHERE column = 'test'";
$result = mysql_query($sql) or die(mysql_error());
echo '<div id="test">';
$i = 0;
while($row = mysql_fetch_assoc($result)){
  if($row['type'] == 3){
    echo '<div style="margin-bottom:20px;">' . random_custom_function($row['val']) . '</div>';
    $i++;
  }
  else {
    echo '<div style="margin-bottom:20px;">' . $row['val'] . '</div>';
  }
}
if($i == 0) {
  echo '<table>';
  echo '<tr><td>Found none!</td></tr>';
  echo '</table>';
}
```

Faria a refatoração seguindo boas práticas de desenvolvimento, facilitando a manutenção e melhorando a segurança da aplicação como:

- Utilizaçao da classe PDO para gerenciar a conexão com o banco de dados, o que torna o acesso mais seguro.
- Implementação de tratamento de exceções para garantir que erros no banco não sejam expostos aos usuários.
- Separação das responsabilidades em duas classes: uma para a conexão (Database) e outra para os usuários (UserRepository), tornando o código mais organizado e fácil de manter.
- Também garantimos a segurança das saídas HTML utilizando htmlspecialchars() para evitar vulnerabilidades de XSS.
- O HTML estruturado de forma separada da lógica e das regras de negócio, o que melhora a legibilidade e a manutenção do front-end.

## Raciocínio Lógico

### 11) Considere a seguinte proposição:

*“Apenas um entre João e José viajou.”*

**A negação da proposição dada acima é logicamente equivalente à proposição:**  

a) João e José viajaram.  
b) João ou José não viajou.  
c) Nem João nem José viajaram.  
d) No máximo, um entre João e José viajou.  
e) João e José viajaram, ou ambos não viajaram.  

***Resposta:*** e) João e José viajaram, ou ambos não viajaram.

### 12) Uma fila na lanchonete da escola é formada por cinco amigos: André, Bernardo, Carlos, Daniel e Eduardo.

André, Daniel e Eduardo estão conversando, ainda que nenhum dos três esteja em uma posição da fila imediatamente ao lado da posição do outro. Eduardo não está em algum extremo da fila, e Carlos está mais à frente na fila do que Bernardo. Daniel está imediatamente atrás de Bernardo se, e somente se,

a) André estiver atrás de Carlos ou Bernardo.  
b) Bernardo estiver na frente de Eduardo.  
c) Daniel estiver na frente de Eduardo.  
d) André estiver na frente de Carlos.  
e) Carlos estiver atrás de Eduardo.  

**Resposta:** b) Bernardo estiver na frente de Eduardo

### 13) Considere as seguintes premissas:

• Se João está na praia ou no cinema, então ele tem febre.  
• Se João não está no cinema, então ele está namorando.  
• Se João está soluçando, então ele está na praia ou não está namorando.  

**Conclui-se que “João ter febre” é uma condição necessária para ele:**

a) Estar no cinema, mas não estar na praia.  
b) Não estar na praia nem no cinema.  
c) Estar namorando.  
d) Não soluçar.  
e) Soluçar.  

**Resposta:** c) Estar namorando.

### 14) Considere a seguinte implicação:

*“Se todos compareceram, então algo deu errado.”*  

Essa implicação é logicamente equivalente à implicação:  

a) Se nada deu certo, então ninguém compareceu.  
b) Se ninguém compareceu, então nada deu errado.  
c) Se todos não compareceram, então algo deu certo.  
d) Se nada deu errado, então alguém não compareceu.  
e) Se algo não deu errado, então alguém não compareceu.  

**Resposta:** d) Se nada deu errado, então alguém não compareceu.

### 15) Sou casado. Tenho dois filhos gêmeos, de 20 anos, fruto do meu primeiro relacionamento.

Uma inferência plausível a partir do texto é:  

a) Seu autor tem pelo menos 38 anos.  
b) Seu autor casou-se apenas uma vez.  
c) Seu autor casou-se pelo menos duas vezes.  
d) Seu autor tem apenas dois filhos do sexo masculino.  
e) Seu autor tem pelo menos um filho do sexo masculino.

**Resposta:** c) Seu autor casou-se pelo menos duas vezes.

## Inteligência Artificial

### 16) Como você integraria o ChatGPT, Gemini ou o CoPilot com o PHP em um sistema de análise de risco onde o risco é avaliado por palavras negativas associadas a um nome pesquisado na internet. Explique como você faria o processamento dos artigos encontrados na internet. (nível médio)

**Resposta:**  
Para integrar o ChatGPT, Gemini ou CoPilot com PHP em um sistema de análise de risco, eu começaria utilizando as APIs disponíveis dessas plataformas para realizar a comunicação entre o PHP e os modelos de IA. A coleta de dados seria feita por meio de web scraping, usando ferramentas como Goutte ou Simple HTML DOM, ou, alternativamente, via APIs de busca como Google ou Bing para obter artigos e notícias relacionadas ao nome pesquisado. Após coletar esses textos, enviaria trechos relevantes para a API da IA através de requisições HTTP utilizando a biblioteca HTTP Guzzle do PHP, onde a IA avaliaria a presença de palavras ou contextos negativos no conteúdo. A IA retornaria uma análise textual, identificando termos que podem indicar risco, e esse resultado seria processado no backend, onde eu aplicaria uma lógica de pontuação para calcular um índice de risco, considerando a frequência e a gravidade dos termos encontrados. Esse índice seria armazenado em uma tabela do banco de dados para consultas posteriores e relatórios, facilitando o acompanhamento contínuo do risco associado ao nome analisado.

### 17) O que é uma base de dados vetorial e como você usaria em uma plataforma de e-commerce ou em um sistema de investimentos? (nível difícil)

**Resposta:**  
Embora eu nunca tenha implementado uma aplicação utilizando uma base de dados vetorial, fiz algumas pesquisas e compreendi o conceito. Uma base de dados vetorial armazena informações de maneira otimizada para permitir buscas semânticas e recomendações baseadas em similaridade, utilizando vetores de características extraídas de dados como texto, imagens ou outros objetos complexos. Cada item é convertido em um vetor numérico, e operações de similaridade, como busca por vizinhos mais próximos (k-NN), são realizadas para encontrar itens relacionados.

Em uma plataforma de e-commerce, pode ser utilizada uma base de dados vetorial para melhorar a experiência de recomendação de produtos. Produtos poderiam ser convertidos em vetores baseados em descrições, imagens ou histórico de interações dos usuários. Com isso, seria possível sugerir itens similares ou personalizar recomendações com base no comportamento do cliente, tornando a busca mais precisa e relevante.

Em um sistema de investimentos, a base de dados vetorial poderia ser utilizada para comparar padrões de desempenho de ativos financeiros. Transformando dados históricos, relatórios ou perfis de risco em vetores, seria possível identificar ativos semelhantes ou correlacionados, ajudando a sugerir investimentos com base no perfil do investidor ou em padrões de mercado detectados.















