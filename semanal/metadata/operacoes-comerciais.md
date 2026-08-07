# Tabelas de Operações Comerciais (Compras/Vendas)

## Introdução

É necessário para a  personalização de um projeto comercial, além de conhecer as regras de negócios, a estrutura do banco de dados.

Deter conhecimento sobre as tabelas associadas e as ligações entre os campos é importante para extrair bons resultados Definir a tabela principal e os principais campos de relacionamento é o primeiro passo para a construção de um DER que verifica o volume de vendas, por exemplo.

O DER abaixo representa as relações entre as tabelas utilizadas para analisar as vendas por produto, com a principal tabela sendo a TGFCAB, juntamente com a TGFITE, que contém as informações pertinentes aos produtos, quantidades e os valores atribuídos.

As duas instâncias, apresentam todas chaves estrangeiras (FK) necessárias para realização das ligações pertinentes aos processos.

O processo de compras e venda são similares e grande parte das instâncias são utilizadas nos dois processos. A diferenciação fica por alguns pontos como:

* parametrizações nos campos da tabela TGFTOP;
* uso das instância de preços TGFTAB e TGFEXC para vendas;
* uso das instância de preços TGFCUS e TGFCUSITE para compras;

O DER apresenta o seguinte conjunto de tabelas:

* **TGFCAB**
* **TGFTOP**
* **TGFITE**
* **TGFPRO**
* **TGFGRU**
* **TGFVEN**
* **TGFPAR**
* **TGFTAB**
* **TGFEXC**
* **TGFCUS**
* **TGFCUSITE**
* **TGFTPV**
* **TGFLOC**
* **TGFEST**
* **TGFVAR**

<Image title="der_png.png" alt={1368} width="100%" border={true} src="https://files.readme.io/e541ae1-der_png.png">
  DER (Compras/Vendas)
</Image>

Diagrama em alta resolução disponível neste [link](https://drive.google.com/file/d/1MmOFY5-mfFj2eu14VqrG3yIgANoJ_k8m/view?usp=sharing).

As tabelas abaixo apresentam informações detalhadas do DER, são apresentadas colunas pertinentes ao processo de vendas ou compras, descrição dos campos, tipo de dado, se as colunas apresentam nulos e valores padrões.

## TGFCAB

A **TGFCAB** é a instância que corresponde ao cabeçalho da nota, e recebe grande parte das chaves estrangeiras (FK) de outras tabelas relacionadas a ela. Ligada a ela, através da chave primária NUNOTA, temos a TGFITE. Essa ligação permite ao usuário elaborar uma visão, tanto do prisma comercial, financeiro ou gerencial.

A TGFCAB possui campos de datas importantes, como por exemplo:

* **DTNEG** - quando utilizado em operações de vendas, indica data de negociação da operação de saída. Já em operações de compras, é preenchido com a data de emissão da nota de compra emitida pelo fornecedor.

* **DTENTSAI** - usualmente utilizado em operações de compras, indicando o registro do dia em que a nota de compra é lançado no ERP Sankhya.

* **DTMOV** - é usado com o mesmo intuito do campo DTENTSAI, porém, mais utilizado em operações contábeis (registros contábeis) e atualização de estoque, registrando a entrada de estoque no dia indicado, dentro do ERP Sankhya.

> 📘 Dica Importante
>
> Para criação de filtros em relatórios destinados a operação de vendas, indica-se o campo DTNEG.

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição do Campo
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUNOTA (PK)
      </td>

      <td>
        Número Único
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODEMP (FK)
      </td>

      <td>
        Código Empresa
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODCENUS (FK)
      </td>

      <td>
        Código do Centro de Resultado
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        NUNNOTA
      </td>

      <td>
        Número da Nota
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DTNEG
      </td>

      <td>
        Data Negociação
      </td>

      <td>
        DATE
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DTFATUR
      </td>

      <td>
        Data de Faturamento
      </td>

      <td>
        DATE
      </td>

      <td>
        S
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DTENTSAI
      </td>

      <td>
        Data de Entrada e Saída
      </td>

      <td>
        DATE
      </td>

      <td>
        S
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODPARC
      </td>

      <td>
        Código do Parceiro
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODTIPOPER
      </td>

      <td>
        Tipo de Operação
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DHTIPOPER
      </td>

      <td>
        Data de Alteração da tabela TGFTOP
      </td>

      <td>
        DATE
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        TIPMOV
      </td>

      <td>
        Tipo de Movimento
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'P'
      </td>
    </tr>

    <tr>
      <td>
        CODTIPVENDA (FK)
      </td>

      <td>
        Código de Tipo de Negociação
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        DHTIPVENDA (FK)
      </td>

      <td>
        Data de Alteração do Tipo de Negociação
      </td>

      <td>
        DATE
      </td>

      <td>
        N
      </td>

      <td>
        TO\_DATE('01/01/1998', 'DD/MM/YYYY')
      </td>
    </tr>

    <tr>
      <td>
        CODVEND
      </td>

      <td>
        Código do Vendedor
      </td>

      <td>
        NUMBER
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        OBSERVACAO
      </td>

      <td>
        Observações
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        S
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        VLOUTROS
      </td>

      <td>
        Outros Valores
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRDESCTOT
      </td>

      <td>
        Desconto no Total
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRDESCTOTITEM
      </td>

      <td>
        Valor de Desconto nos Itens
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRFRETE
      </td>

      <td>
        Valor de Frete
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        TIPFRETE
      </td>

      <td>
        Tipo de Frete
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'S'
      </td>
    </tr>

    <tr>
      <td>
        VLRNOTA
      </td>

      <td>
        Valor da Nota
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        ORDEMCARGA
      </td>

      <td>
        Ordem de carga
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODPARCTRANSP
      </td>

      <td>
        Código do Parceiro Transportador
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        BASEICMS
      </td>

      <td>
        Base ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRICMS
      </td>

      <td>
        Valor ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        BASEIPI
      </td>

      <td>
        Base IPI
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRIPI
      </td>

      <td>
        Valor do IPI
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        STATUSNOTA
      </td>

      <td>
        Status da Nota
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'P'
      </td>
    </tr>

    <tr>
      <td>
        PERCDESC
      </td>

      <td>
        Percentual de Desconto
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODNAT
      </td>

      <td>
        Código de Natureza
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CHAVENFE
      </td>

      <td>
        Chave NF-e
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        STATUSNFE
      </td>

      <td>
        Status NF-e
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFTOP

Instância onde ocorre a parametrizações dos processos de entradas ou saídas, registros financeiros e movimentos de estoque. A ligação entre a TGFTOP e a TGFCAB apresenta pontos importantes, que devem ser analisados:

* relacionamento entre o campo DHTIPOPER da tabela TGFCAB e o campo DHALTER da tabela TGFTOP.

* ligação entra a chave estrangeira CODTIPOPER da tabela TGFCAB e a chave primária do campo CODTIPOPER da tabela TGTOP.

> 📘 Informação Importante
>
> O campo DHALTER armazena parametrizações, dando a TGFTOP a condição de uma tabela de armazenamento histórico.

O detalhe importante que existe na TGFTOP é que ela é conhecida como uma tabela histórica, guardando cada parametrização através do campo DHALTER da TGFTOP, logo cada vendas irá registrar as parametrizações criadas com o decorrer do tempo.

Por exemplo: Se parametrizarmos a TGFTOP de venda para não gerar financeiro e criarmos uma venda no Portal de Vendas, essa nota não irá gerar o financeiro, e no campo DHTIPOPER da TGFCAB estará o registro da data e hora em que essa parametrização foi realizada.

Se voltarmos na TGFTOP e alterarmos para que ela gere financeiro como receita, o campo DHALTER registrará a data e hora dessa nova parametrização e todas as próximas vendas realizadas começarão a gerar financeiro do tipo receita. Porém a venda realizada na parametrização anterior permanecerá imutável, pois a parametrização anterior permaneceu igual e a venda realizada naquele momento dizia que não geraria financeiro.

Isso é o efeito histórico que essa tabela possui, sendo possível o registro de todas as parametrizações realizadas no decorrer do tempo.

```sql
FROM
TGFCAB CAB
inner join TGFTOP TPO on CAB.CODTIPOPER = TPO.CODTIPOPER and CAB.DHTIPOPER = TPO.DHALTER 🟢🟢🟢
```

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição do Campo
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        CODTIPOPER (PK)
      </td>

      <td>
        Código Tipo de Operação
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DHALTER (PK)
      </td>

      <td>
        Data Alteração
      </td>

      <td>
        DATE
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DESCROPER
      </td>

      <td>
        Descrição Tipo de Operação
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        TIPMOV
      </td>

      <td>
        Tipo de Movimento
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'P'
      </td>
    </tr>

    <tr>
      <td>
        ATUALFIN
      </td>

      <td>
        Atualiza Financeiro
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        Y
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        TIPATUALFIN
      </td>

      <td>
        Tipo de Atualização do Financeiro
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        'I'
      </td>
    </tr>

    <tr>
      <td>
        ATUALCOM
      </td>

      <td>
        Atualiza Comissão
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'N'
      </td>
    </tr>

    <tr>
      <td>
        ATUALEST
      </td>

      <td>
        Atualiza Estoque
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        'N'
      </td>
    </tr>

    <tr>
      <td>
        GOLSINAL
      </td>

      <td>
        Gerente Online Sinal
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        GOLDEV
      </td>

      <td>
        Gerente Online Devolução
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        1
      </td>
    </tr>

    <tr>
      <td>
        NFE
      </td>

      <td>
        NF-e
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFITE

Nessa instância tem-se informações das quantidades negociadas, através do campo QTDNEG e do preço de venda do produto, através do campo VLRUNIT. O resultado dessa operação resulta no VLRTOT.

> 📘 Informações Importantes
>
> * Utiliza-se o campo VLRTOT para determinar o valor total dos itens negociados, ao invés de realizar a multiplicação dos campos QTDNEG e VLRUNIT.
>
> * Para se obter o valor total líquido da venda do produto, utiliza-se o desconto atribuído ao item, realizando a subtração dos campos (VLRTOT – VLRDESC).

```sql
FROM
TGFCAB CAB
inner join TGFTOP TPO on CAB.CODTIPOPER = TPO.CODTIPOPER and CAB.DHTIPOPER = TPO.DHALTER
inner join TGFITE ITE on CAB.NUNOTA = ITE.NUNOTA 🟢🟢🟢
```

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição do Campo
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUNOTA (PK)
      </td>

      <td>
        Número Único
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        SEQUENCIA (PK)
      </td>

      <td>
        Sequência
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODEMP (FK)
      </td>

      <td>
        Código de Empresa
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODPROD (FK)
      </td>

      <td>
        Código de Produto
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODLOCALORIG (FK)
      </td>

      <td>
        Código Local Origem
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Controle
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        ..
      </td>
    </tr>

    <tr>
      <td>
        CODCFO (FK)
      </td>

      <td>
        Código de CFOP
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        QTDNEG
      </td>

      <td>
        Quantidade Negociada
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        QTDENTREGUE
      </td>

      <td>
        Quantidade Entregue
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRUNIT
      </td>

      <td>
        Valor Unitário
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRTOT
      </td>

      <td>
        Valor Total
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        BASEIPI
      </td>

      <td>
        Base de IPI
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRIP
      </td>

      <td>
        Valor de IPI
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRICMS
      </td>

      <td>
        Valor ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        VLRDESC
      </td>

      <td>
        Valor Desconto
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        ALIQICMS
      </td>

      <td>
        Alíquota de ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        ALIQIPI
      </td>

      <td>
        Alíquota de IPI
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        PENDENTE
      </td>

      <td>
        Pendente
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'S'
      </td>
    </tr>

    <tr>
      <td>
        CODVOL (FK)
      </td>

      <td>
        Código de Volume
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        '0'
      </td>
    </tr>

    <tr>
      <td>
        CODTRIB
      </td>

      <td>
        Código de Tributação
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        PERCDESC
      </td>

      <td>
        Percentual de Desconto
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>
  </tbody>
</Table>

## TGFPRO

Instância responsável por centralizar informações a respeito dos produtos inseridos no ERP Sankhya. Para trazer informações do cadastro de produtos, relaciona-se a chave estrangeira CODPROD da tabela TGFITE com a chave primária CODPROD da tabela TGFPRO. Ao realizar essa ação se obtém informações como a descrição do produto e sua marca.

```sql
FROM
TGFCAB CAB
inner join TGFTOP TPO on CAB.CODTIPOPER = TPO.CODTIPOPER and CAB.DHTIPOPER = TPO.DHALTER
inner join TGFITE ITE on CAB.NUNOTA = ITE.NUNOTA
inner join TGFPRO PRO on ITE.CODPROD = PRO.CODPROD 🟢🟢🟢
```

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        CODPROD (PK)
      </td>

      <td>
        Código do Produto
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DESCRPROD
      </td>

      <td>
        Descrição do Produto
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        REFERENCIA
      </td>

      <td>
        Referência
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODGRUPOPROD
      </td>

      <td>
        Código do Grupo de Produto
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODVOL
      </td>

      <td>
        Código do Volume
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        MARCA
      </td>

      <td>
        Marca
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        COMVEND
      </td>

      <td>
        Comissão de Venda
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DESCMAX
      </td>

      <td>
        Desconto Máximo
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        USOPROD
      </td>

      <td>
        Usado Como
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        'V'
      </td>
    </tr>

    <tr>
      <td>
        TIPOCONTEST
      </td>

      <td>
        Tipo de Controle de Estoque
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        'N'
      </td>
    </tr>

    <tr>
      <td>
        ESTMAX
      </td>

      <td>
        Estoque Máximo
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        ESTMIN
      </td>

      <td>
        Estoque Mínimo
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODPARCFORN (FK)
      </td>

      <td>
        Código Parceiro Fornecedor
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        REFFORN
      </td>

      <td>
        Referência do Fornecedor
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        NCM
      </td>

      <td>
        NCM
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODLOCALPADRAO
      </td>

      <td>
        Código do Local Padrão
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFGRU

Através do relacionamento da instância TGFPRO, é possível relacionar o grupo de produto, trazendo informações como a descrição do grupo em que ele está inserido. O processo se dá através da chave estrangeira CODGRUPOPROD da tabela TGFPRO com a chave primária CODGRUPOPROD da tabela TGFGRU.

```sql
FROM
TGFCAB CAB
inner join TGFTOP TPO on CAB.CODTIPOPER = TPO.CODTIPOPER and CAB.DHTIPOPER = TPO.DHALTER
inner join TGFITE ITE on CAB.NUNOTA = ITE.NUNOTA
inner join TGFPRO PRO on ITE.CODPROD = PRO.CODPROD
inner join TGFGRU GRU on PRO.CODGRUPOPROD = GRU.CODGRUPOPROD 🟢🟢🟢
```

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        CODGRUPOPROD
      </td>

      <td>
        Código do Grupo de Produto
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DESCRGRUPOPROD
      </td>

      <td>
        Descrição do Grupo de Produto
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODGRUPAI
      </td>

      <td>
        Código do Grupo Pai
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        GRAU
      </td>

      <td>
        Grau
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFVEN

Nas vendas realizadas, obtém-se o registro do vendedor através do campo CODVEND da TGFCAB. Para se ter o nome do vendedor (campo APELIDO), é necessário realizarmos a ligação da chave estrangeira CODVEND da TGFCAB com a chave primária CODVEND da TGFVEN.

```sql
FROM
TGFCAB CAB
inner join TGFTOP TPO on CAB.CODTIPOPER = TPO.CODTIPOPER and CAB.DHTIPOPER = TPO.DHALTER
inner join TGFITE ITE on CAB.NUNOTA = ITE.NUNOTA
inner join TGFPRO PRO on ITE.CODPROD = PRO.CODPROD
inner join TGFGRU GRU on PRO.CODGRUPOPROD = GRU.CODGRUPOPROD
inner join TGFVEN VEN on CAB.CODVEND = VEN.CODVEND 🟢🟢🟢
```

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        CODVEND (PK)
      </td>

      <td>
        Código do Vendedor
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        TIPVEND
      </td>

      <td>
        Tipo de Vendedor
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        APELIDO
      </td>

      <td>
        Apelido
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODPARC (FK)
      </td>

      <td>
        Código do Parceiro
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        COMVENDA
      </td>

      <td>
        Comissão de Venda
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        COMGER
      </td>

      <td>
        Comissão de Gerente
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODEMP (FK)
      </td>

      <td>
        Código da Empresa
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFPAR

A instância de parceiros se relaciona com a tabela TGFCAB através da chave estrangeira CODPARC, ligando-as através da chave primária CODPARC da tabela TGFPAR.

```sql
FROM
TGFCAB CAB
inner join TGFTOP TPO on CAB.CODTIPOPER = TPO.CODTIPOPER and CAB.DHTIPOPER = TPO.DHALTER
inner join TGFITE ITE on CAB.NUNOTA = ITE.NUNOTA
inner join TGFPRO PRO on ITE.CODPROD = PRO.CODPROD
inner join TGFGRU GRU on PRO.CODGRUPOPROD = GRU.CODGRUPOPROD
inner join TGFVEN VEN on CAB.CODVEND = VEN.CODVEND
inner join TGFPAR PAR on CAB.CODPARC = PAR.CODPARC 🟢🟢🟢
```

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        CODPARC (PK)
      </td>

      <td>
        Código do Parceiro
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        NOMEPARC
      </td>

      <td>
        Nome do Parceiro
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        RAZAOSOCIAL
      </td>

      <td>
        Razão Social
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        TIPPESSOA
      </td>

      <td>
        Tipo de Pessoa
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODEND (FK)
      </td>

      <td>
        Código do Endereço
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        NUMEND
      </td>

      <td>
        Número
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODBAI (FK)
      </td>

      <td>
        Código do Bairro
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODCID (FK)
      </td>

      <td>
        Código da Cidade
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CEP
      </td>

      <td>
        CEP
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        TELEFONE
      </td>

      <td>
        Telefone
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        EMAIL
      </td>

      <td>
        E-mail
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DTNASCIMENTO
      </td>

      <td>
        Data de Nascimento
      </td>

      <td>
        DATE
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        IDENTINSCESTAD
      </td>

      <td>
        Identidade/Inscrição Estadual
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CGC\_CPF
      </td>

      <td>
        CNJP/CPF
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODTAB (FK)
      </td>

      <td>
        Código da Tabela de Preço
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CLIENTE
      </td>

      <td>
        Nome Cliente
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'S'
      </td>
    </tr>

    <tr>
      <td>
        FORNECEDOR
      </td>

      <td>
        Fornecedor
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'N'
      </td>
    </tr>

    <tr>
      <td>
        LIMCRED
      </td>

      <td>
        Limite de Crédito
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        SEXO
      </td>

      <td>
        Sexo
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFTAB

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUTAB (PK)
      </td>

      <td>
        Código da Tabela de Preço
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODTAB
      </td>

      <td>
        Código da Tabela de Preço
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        DTVIGOR
      </td>

      <td>
        Data de Vigor
      </td>

      <td>
        DATE
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DTALTER
      </td>

      <td>
        Data de Alteração
      </td>

      <td>
        DATE
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        PERCENTUAL
      </td>

      <td>
        Percentual
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODTABORIG
      </td>

      <td>
        Código da Tabela de Preço Origem
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        Y
      </td>

      <td>
        0
      </td>
    </tr>
  </tbody>
</Table>

## TGFEXC

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUTAB (PK)
      </td>

      <td>
        Código da Tabela de Preço
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODPROD (PK)
      </td>

      <td>
        Código do Produto
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODLOCAL (PK)
      </td>

      <td>
        Código do Local
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE (PK)
      </td>

      <td>
        Controle
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        ' '
      </td>
    </tr>

    <tr>
      <td>
        VLRVENDA
      </td>

      <td>
        Preço
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        'V'
      </td>
    </tr>

    <tr>
      <td>
        TIPO
      </td>

      <td>
        Tipo
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFCUS

Na parametrização do processo de compras é comum criarmos fórmulas em que os valores de custos fiscais e gerenciais são formados automaticamente.

Isso ocorre através da inserção do histórico das entradas (de acordo com a empresa, local ou controle e regras de negócio do parceiro) a tabela TGFCUS.

A instância TGFCUS apresenta os valores de custos registrados, estes formados pelas fórmulas de custo e preço.

```sql
FROM
TGFCAB CAB
inner join TGFITE ITE on CAB.NUNOTA = ITE.NUNOTA
inner join TGFCUSITE CUS on ITE.NUNOTA = CUS.NUNOTA AND ITE.SEQUENCIA = CUS.SEQUENCIA 🟢🟢🟢
```

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        CODPROD (PK) (FK)
      </td>

      <td>
        Número Único
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODEMP (PK) (FK)
      </td>

      <td>
        Código Empresa
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        DTATUAL (PK)
      </td>

      <td>
        Data Atual
      </td>

      <td>
        DATE
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CODLOCAL (PK) (FK)
      </td>

      <td>
        Local
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE (PK)
      </td>

      <td>
        Controle
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        ' '
      </td>
    </tr>

    <tr>
      <td>
        CUSMEDICM
      </td>

      <td>
        Custo Médio com ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CUSSEMICM
      </td>

      <td>
        Custo Médio sem ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CUSREP
      </td>

      <td>
        Custo de Reposição
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CUSVARIAVEL
      </td>

      <td>
        Número Único
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CUSGER
      </td>

      <td>
        Sequência
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CUSMED
      </td>

      <td>
        Custo de Reposição
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        ENTRADACOMICMS
      </td>

      <td>
        Último Custo sem ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        ENTRADASEMMICMS
      </td>

      <td>
        Último Custo com ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        NUNOTA
      </td>

      <td>
        Número Único
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        SEQUENCIA
      </td>

      <td>
        Sequência
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>
  </tbody>
</Table>

## TGCUSITE

A instância TGFCUSITE,  corresponde ao custo por item, apresenta os mesmos registros presentes na TGFCUS, porém aqui são apresentados somente os itens de uma compra lançada, possibilitando a busca de notas através da chave primária composta NUNOTA e SEQUENCIA.

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUNOTA (PK)
      </td>

      <td>
        Número Único
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        SEQUENCIA (PK)
      </td>

      <td>
        Sequência
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODPROD (PK)
      </td>

      <td>
        Código Produto
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODEMP
      </td>

      <td>
        Código Empresa
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODLOCAL
      </td>

      <td>
        Data Atual
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Local
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        ' '
      </td>
    </tr>

    <tr>
      <td>
        DTATUAL
      </td>

      <td>
        Controle
      </td>

      <td>
        DATE
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        CUSGER
      </td>

      <td>
        Custo Médio com ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CUSVARIAVEL
      </td>

      <td>
        Custo Médio sem ICMS
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        DUSREP
      </td>

      <td>
        Custo de Reposição
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        ENTRADACOMICMS
      </td>

      <td>
        Número Único
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        ENTRADASEMICMS
      </td>

      <td>
        Sequência
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>
  </tbody>
</Table>

## TGFTPV

Na instância de tipos de negociações estão cadastradas as formas de pagamentos utilizadas nas operações em que existam financeiro. Ela apresenta a mesma característica de armazenamento histórico, registrando historicamente cada alteração realizada, inserindo uma nova linha de acordo com a data de alteração utilizando o campo.

> 📘 Dica Importante
>
> Ao iniciar uma nota de venda ou compra, se for necessário realizar alguma alteração no tipo de negociação, exclui-se a nota e cria-se uma nova. Isso garante que as alterações ocorram, pois na TGFCAB também é registrado a data de alteração do tipo de negociação, através do campo DHTIPVENDA.

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        CODTIPVENDA (PK)
      </td>

      <td>
        Código do Tipo de Venda
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        DHALTER (PK)
      </td>

      <td>
        Data e hora alteração
      </td>

      <td>
        Date
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DESCRTIPVENDA
      </td>

      <td>
        Descrição
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        SUBTIPOVENDA
      </td>

      <td>
        Subtipo
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        VENDAMIN
      </td>

      <td>
        Valor mínimo para venda
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        TAXAJURO
      </td>

      <td>
        Taxa em %
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DESCMAX
      </td>

      <td>
        % Desconto Máximo
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DESCPROM
      </td>

      <td>
        Desconto Promocional
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        Y
      </td>

      <td>
        'S'
      </td>
    </tr>

    <tr>
      <td>
        PRAZOMIN
      </td>

      <td>
        Prazo Mínimo
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        Y
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFLOC

Na instância TGFLOC, são cadastrados os espaços físicos ou gerenciais em que produtos são armazenados.\
Dividem-se em dois grupos:

* Físicos: armazéns, depósitos ou a própria empresa;
* Gerencial: avaria, separação ou site;

O local de armazenamento, pode ser lançado em operações de compra e vendas. Em compras, é realizado no processo de entrada de estoque no local selecionado, enquanto em vendas, quando há baixa de estoque.

Uma terceira opção é quando há transferência de estoque, que realiza as duas operações (compras/vendas) ao mesmo tempo e em locais distintos.

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        CODLOCAL (PK)
      </td>

      <td>
        Código do Tipo de Venda
      </td>

      <td>
        Number (10)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        DESCRLOCAL
      </td>

      <td>
        Descrição
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        ANALITICO
      </td>

      <td>
        Analítico
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'S'
      </td>
    </tr>

    <tr>
      <td>
        GRAU
      </td>

      <td>
        Grau
      </td>

      <td>
        Number (5)
      </td>

      <td>
        N
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFEST

A instância TFGEST (estoque) registra as quantidades que cada produto possui armazenado, podendo esse estoque ser detalhado por suas chaves primárias.

A parametrização podendo ocorrer por empresa, local, controle, parceiro e tipo (próprio do parceiro ou de terceiros).

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        CODEMP (PK) (FK)
      </td>

      <td>
        Código da Empresa
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODLOCAL (PK) (FK)
      </td>

      <td>
        Código do Local
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CODPROD (PK) (FK)
      </td>

      <td>
        Código do Produto
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE (PK)
      </td>

      <td>
        Controle
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        ' '
      </td>
    </tr>

    <tr>
      <td>
        RESERVADO
      </td>

      <td>
        Reservado
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        S
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        ESTMIN
      </td>

      <td>
        Estoque Mínimo
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        ESTMAX
      </td>

      <td>
        Estoque Máximo
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        DTVAL
      </td>

      <td>
        Data de Validade
      </td>

      <td>
        DATE
      </td>

      <td>
        S
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        TIPO (PK)
      </td>

      <td>
        Tipo
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'P'
      </td>
    </tr>

    <tr>
      <td>
        CODPARC (PK) (FK)
      </td>

      <td>
        Código do Parceiro
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        ESTOQUE
      </td>

      <td>
        Estoque
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        DTFABRICACAO
      </td>

      <td>
        Data de Fabricação
      </td>

      <td>
        DATE
      </td>

      <td>
        S
      </td>

      <td>
        (null)
      </td>
    </tr>
  </tbody>
</Table>

## TGFVAR

Instância que realiza a ligação entre orçamentos e pedidos, pedidos e notas, notas e devoluções. Ela utiliza os campos NUNOTAORIG (número único de origem) e o NUNOTA (número único destino), além dos campos SEQUENCIAORIG e SEQUENCIA.

Ela é utilizada para registrar também os possíveis vários faturamentos parciais que possam ocorrer entre pedidos e notas, como também de notas e devoluções.

Por exemplo, no ato da geração de um pedido de venda, a empresa pode não ter todos os itens no ato da venda e negociar com o cliente o faturamento parcial apenas dos produtos em estoque.

Logo um único pedido pode ser faturado em várias notas de venda, com isso, a TGFVAR terá vários números únicos de destino (vendas) para apenas um número único de origem (o pedido de venda).

<Table align={["left","left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Nome da Coluna
      </th>

      <th>
        Descrição da Coluna
      </th>

      <th>
        Tipo de Dado
      </th>

      <th>
        NULO
      </th>

      <th>
        DEFAULT
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUNOTA
      </td>

      <td>
        Número Único
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        SEQUENCIA
      </td>

      <td>
        Sequência
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        NONOTAORIG
      </td>

      <td>
        Número Único Origem
      </td>

      <td>
        NUMBER (10)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        SEQUENCIAORIG
      </td>

      <td>
        Sequência Origem
      </td>

      <td>
        NUMBER (5)
      </td>

      <td>
        N
      </td>

      <td>
        0
      </td>
    </tr>

    <tr>
      <td>
        QTDATENDIDA
      </td>

      <td>
        Quantidade Atendida
      </td>

      <td>
        FLOAT (126)
      </td>

      <td>
        S
      </td>

      <td>
        (null)
      </td>
    </tr>

    <tr>
      <td>
        STATUSNOTA
      </td>

      <td>
        Status da Nota
      </td>

      <td>
        VARCHAR2
      </td>

      <td>
        N
      </td>

      <td>
        'P'
      </td>
    </tr>
  </tbody>
</Table>

## Dicas para criação de relatórios

No processo de criação relatórios para parceiros Sankhya, deve-se ter em mente que grande parte não será possível  o reaproveitamento, pois existe nuances específicas para cada negócio. Indica-se realizar um levantamento com os usuários que irão utilizar os relatórios, e documentar os detalhes a fim de validar o escopo.

> 📘 Dica Importante
>
> Em processos comerciais(compra ou venda) é necessário relacionar as condições dos filtros de vendedor, grupo de produtos e parceiros, tendo como requisito funcional a não obrigatoriedade desses filtros.

Na realização de queries para consulta, dentro cláusula WHERE, deve-se colocar a seguinte sequência:

* campo a ser filtrado seguido do operador de igualdade;
* parâmetro seguido do operador booleano OR seguido da condição IS NULL;

Tudo deve ser realizado dentro de parênteses visto que há envolvimento do operador lógico OR.

```sql
WHERE
	CAB.DTNEG BETWEEN :PERIODOINI and :PERIODOFIN
	AND (CAB.CODVEND = :CODVEND or :CODVEND IS NULL)🟢🟢🟢
	AND (CAB.CODPARC = :CODPARC or :CODPARC IS NULL)🟢🟢🟢
	AND (PRO.CODGRUPOPROD = :CODGRUPOPROD or :CODGRUPOPROD IS NULL)🟢🟢🟢
```

> 📘 Informação Importante
>
> Com o detalhamento dos relacionamentos das tabelas na consulta acima, é possível desenvolver relatórios com as especificidades solicitadas pelos usuários finais do ERP Sankhya.

## Como tirar dúvidas?

Para tirar dúvidas e compartilhar informações, use a sala [Banco de dados](https://comunidade.sankhya.com.br/c/sdk/banco-de-dados/7) da comunidade Sankhya Developer.