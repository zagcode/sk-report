> ## Documentation Index
> Fetch the complete documentation index at: https://developer.sankhya.com.br/llms.txt
> Use this file to discover all available pages before exploring further.

# Dicionário de Dados

## Introdução ao Dicionário de Dados

O dicionário de dados é um dos componentes mais fundamentais da plataforma Sankhya, ele é composto por um conjunto de tabelas que provêm informações sobre as demais tabelas do banco de dados. Dessa forma, o dicionário de dados se configura como um repositório de metadados, armazenados em um banco de dados relacional, que descrevem e mapeiam a estrutura de dados do sistema, englobando informações sobre:

* **Tabelas**
* **Campos**
* **Ligações**
* **Entidades**
* **Propriedades**
* **Regras de domínio**

Incluindo por exemplo, descrições e possíveis valores para campos do sistema. Ele controla também a hierarquia de telas e restrições por licença.

Essa estrutura possibilita o uso de técnicas de programação table-driven, de forma que boa parte do sistema pode ser montada em tempo de execução, por componentes que usam as meta-informações do dicionário de dados como entrada.

Na Sankhya o Dicionário de dados é aplicado em pelos menos três frentes:

**Documentação:** Depois de compreendida a estrutura dos dados, o mapeamento também pode ser consumido como documentação, pois a sua estrutura contém informações sobre o nome, tipo, tamanho, ligações, ou seja, todos os metadados que podem ser utilizados para determinar o comportamento de componentes, persistência, entre outras coisas.

**JAPE:** Framework de persistência. Baseado no conjunto de meta informações o JAPE gera, dinamicamente, as estruturas SQL, como por exemplo: INSERT, UPDATE, DELETE e SELECT.

**Dynaform:** Framework para construção de telas. Baseado nos metadados, o Dynaform possibilita a criação dinâmica de telas sem nenhuma definição de código de backend e front-end.

## Funções do Dicionário de dados

* O sistema consume informações do dicionário de dados para montar suas telas
* O dicionário de dados é atualizado quando melhorias ou novas implementações são realizadas, mantendo a integridade dos dados do sistema
* Todo desenvolvedor pode usar o dicionário de dados como referência para obter informações sobre o banco de dados

## Arquitetura do Dicionário de Dados

O dicionário de dados consiste no seguinte conjunto de tabelas:

* **TDDTAB**
* **TDDCAM**
* **TDDOPC**
* **TDDPCO**
* **TDDINS**
* **TDDLIG**
* **TDDLGC**
* **TRDCON**
* **TRDPCO**
* **TRDFCO**
* **TRDEVE**
* **TDDIAC**
* **TDDTABI18N**
* **TDDCAMI18N**
* **TDDOPCI18N**
* **TDDINSI18N**
* **TRDCONI18N**
* **TDDI18N**

A tabela abaixo apresenta a descrição de cada uma das tabelas do dicionário de dados e alguns dos seus campos e respectivos valores.

## DER - Dicionário de dados

O diagrama a seguir apresenta as entidades do dicionário de dados e suas relações entre si, assim como seus atributos.

<Image title="DER_V1.jpg" alt={1714} align="center" width="smart" border={true} src="https://files.readme.io/f2a4a3d-DER_V1.jpg">
  DER - Dicionário de dados
</Image>

Diagrama em alta resolução disponível neste [link](https://drive.google.com/file/d/1g1Zeh3uQx9urRYBPHtv3P-5a5qBCWB2L/view?usp=share_link).

O diagrama a seguir apresenta as entidades do dicionário de dados e suas relações entre si, assim como seus atributos.

## TDDTAB

A **TDDTAB** contém informações relativas ao mapeamento das tabelas. A chave natural desta tabela é **NOMETAB**.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Campo
      </th>

      <th>
        Descrição
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NOMETAB
      </td>

      <td>
        Nome da tabela.
      </td>
    </tr>

    <tr>
      <td>
        DESCRTAB
      </td>

      <td>
        Descrição da tabela.
      </td>
    </tr>

    <tr>
      <td>
        TIPONUMERACAO
      </td>

      <td>
        Tipo de numeração.  

        A - Automática\
        M - Manual\
        T - Tabela auxiliar
      </td>
    </tr>

    <tr>
      <td>
        NUCAMPONUMERACAO
      </td>

      <td>
        Ligação com a TDDCAM para os metadados do campo.
      </td>
    </tr>

    <tr>
      <td>
        ADICIONAL
      </td>

      <td>
        Define se a tabela é adicional. Usado para artefatos personalizados.
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).
      </td>
    </tr>

    <tr>
      <td>
        NUMOS
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>

    <tr>
      <td>
        LIBERADO
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>
  </tbody>
</Table>

## TDDCAM

Contém informações relativas ao mapeamento dos campos das tabelas. A chave natural desta tabela é **NOMETAB** e **NOMECAMPO**.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Campo
      </th>

      <th>
        Descrição
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUCAMPO
      </td>

      <td>
        Informação de controle interno. Utilizado como identificador único de registro.
      </td>
    </tr>

    <tr>
      <td>
        NOMETAB
      </td>

      <td>
        Nome da tabela.
      </td>
    </tr>

    <tr>
      <td>
        NOMECAMPO
      </td>

      <td>
        Nome do campo.
      </td>
    </tr>

    <tr>
      <td>
        DESCRCAMPO
      </td>

      <td>
        Descrição do campo.
      </td>
    </tr>

    <tr>
      <td>
        TIPCAMPO
      </td>

      <td>
        Define o tipo do campo.  

        * \*B\*\* - Blob: Usado para imagens  
        * \*C \*\*- Clob: Usado para texto longo  
        * \*D\*\* - Date: Usado para datas  
        * \*F \*\*- Float: Usado para valores decimais  
        * \*I \*\*- Integer: Usado para valores inteiros  
        * \*H\*\* - DateTime: Usado para data/hora  
        * \*S\*\* - String: Usado para texto  
        * \*T\*\* - Time: Usado para hora
      </td>
    </tr>

    <tr>
      <td>
        EXPRESSAO
      </td>

      <td>
        Usado para definição de campos calculados. Também pode ser usado para definição de valores padrões em campos não calculados. Podemos criar dois tipos de expressões:  

        **1 - SQL**\
        **2 - BeanShell**
      </td>
    </tr>

    <tr>
      <td>
        PERMITEPESQUISA
      </td>

      <td>
        Indica se o campo permite pesquisa. Geralmente usado dentro de componentes de pesquisa.
      </td>
    </tr>

    <tr>
      <td>
        CALCULADO
      </td>

      <td>
        Define se o campo é calculado. Campos calculados não existem fisicamente nas tabelas, ou seja, não são persistidos.
      </td>
    </tr>

    <tr>
      <td>
        PERMITEPADRAO
      </td>

      <td>
        Indica se o campo permite definição de valor padrão. Geralmente usado na configuração de formulários.
      </td>
    </tr>

    <tr>
      <td>
        APRESENTACAO
      </td>

      <td>
        Define o campo de apresentação da tabela. O campo de apresentação geralmente é usado em campos de pesquisa e nomes de abas relacionadas a ligações de instâncias.
      </td>
    </tr>

    <tr>
      <td>
        ORDEM
      </td>

      <td>
        Define a ordenação do campo. Geralmente usado para ordenar o campo em grades e formulários.
      </td>
    </tr>

    <tr>
      <td>
        VISIVELGRIDPESQUISA
      </td>

      <td>
        Define a visibilidade do campo na grade de pesquisa. Geralmente usado em componentes de pesquisa.
      </td>
    </tr>

    <tr>
      <td>
        TIPOAPRESENTACAO
      </td>

      <td>
        Define o tipo de apresentação do campo.  

        * \*A\*\* - Arquivo  
        * \*C\*\* - Checkbox  
        * \*H\*\* - Formatação HTML  
        * \*I\*\* - Imagem  
        * \*M\*\* - Múltiplos arquivos  
        * \*O\*\* - Lista de opções  
        * \*P\*\* - Padrão  
        * \*T\*\* - Caixa de texto
      </td>
    </tr>

    <tr>
      <td>
        TAMANHO
      </td>

      <td>
        Define o tamanho do campo.
      </td>
    </tr>

    <tr>
      <td>
        ADICIONAL
      </td>

      <td>
        Define se o campo é adicional. Usado para artefatos personalizados.
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).
      </td>
    </tr>

    <tr>
      <td>
        NUMOS
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>

    <tr>
      <td>
        LIBERADO
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>
  </tbody>
</Table>

## TDDOPC

Contém informações relativas ao mapeamento das opções dos campos.

| Campo    | Descrição                                                                                                       |
| :------- | :-------------------------------------------------------------------------------------------------------------- |
| NUCAMPO  | Informação de controle interno. Utilizado como identificador único de registro e chave estrangeira para TDDCAM. |
| OPCAO    | Define, de forma descritiva, a opção do campo.                                                                  |
| VALOR    | Define o valor da opção.                                                                                        |
| PADRAO   | Define a opção padrão.                                                                                          |
| ORDEM    | Define a ordenação da opção.                                                                                    |
| CONTROLE | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).                                            |
| NUMOS    | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.                               |
| LIBERADO | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.                               |

## TDDPCO

Contém informações relativas ao mapeamento de propriedades dos campos.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Campo
      </th>

      <th>
        Descrição
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUCAMPO
      </td>

      <td>
        Informação de controle interno. Utilizado como identificador único de registro e chave estrangeira para TDDCAM.
      </td>
    </tr>

    <tr>
      <td>
        NOME
      </td>

      <td>
        Existem diversas propriedades para funcionalidades diversas.  

        * \*APP\_PROFILE\*\*: Permite definir uma licença de uso. O campo ficará visível apenas se o cliente possuir a licença.  
        * \*cantrim\*\*: Define o valor vazio para os campos do tipo String, caso o seu valor seja nulo. O valor esperado é (true/false).  
        * \*cleanOnCopy\*\*: Define se o campo será copiado pela funcionalidade de duplicação do dataset.  
        * \*dateOnly\*\*: Usado para campos do tipo Data. Força o uso da data sem horas.  
        * \*encodedtransport\*\*: Força o encript do dado antes de apresentar ao usuário.  
        * \*gridFooterOper\*\*: Permite criar um rodapé de coluna. Pode assumir os valores: 1 - count: Contador de linhas; first: Valor da primeira linha; last: Valor da última linha; sum: Totalizador da coluna.  
        * \*metadataInterceptor\*\*: Esta propriedade permite definir um inteceptador de metados em Java. O valor esperado é o nome completo da classe.  
        * \*nuCasasDecimais\*\*: Permite definir a quantidade de casas decimais para os campos do tipo FLOAT. O valor esperado é numérico.  
        * \*readOnly\*\*: Define que o campo é apenas leitura. O valor esperado é (true/false).  
        * \*requerido\*\*: Define a obrigatoriedade do campo. O valor esperado é (true/false).  
        * \*UIGroupName\*\*: Permite definir um agrupador de campos. O valor esperado é o Título do Grupo.  
        * \*UITabName\*\*: Permite definir uma aba para o campo. O valor esperado é o Título da Aba.  
        * \*UIType\*\*: Permite forçar um tipo específico de componente para o campo. O valor esperado é (PASSWORD, CEP, Phone e CGC\_CPF).  
        * \*useSelectDistinct\*\*: Força a criação de um campo de pesquisa. A pesquisa será realizada na própria tabela de origem do campo (SELECT DISTINCT CAMPO FROM TABELA). O valor esperado é (true/false).  
        * \*visivel\*\*: Define a visibilidade do campo. O valor esperado é (true/false).  

        *Propriedades para criar filtro padrão nas telas Dynaform:*  

        * \*filterDefaultValue\*\*: Permite informar um valor padrão.  
        * \*filterGroup\*\*: Permite criar um grupo de filtros.  
        * \*filterLabel\*\*: Define o label do filtro.  
        * \*filterOrder\*\*: Define a ordem do campo filtro.  
        * \*filterRequired\*\*: Define a obrigatoriedade do filtro.  
        * \*filterSql\*\*: Define uma expressão SQL para o filtro.  
        * \*filterType\*\*: Define o tipo do filtro. Podendo assumir os valores “period”, “mult-list” ou “default”. O valor “period” irá criar um filtro do tipo período (intervalo de datas). O valor “mult-list” irá criar uma lista de múltipla seleção. O valor “default” irá usar os metadados do próprio campo para criar o respectivo componente.  

        *Propriedades para definição de metadados adicionais (rowmetada).*  

        * \*rmp\*\*: Define o provedor de metadados.  
        * \*rm\_precision\*\*: Define a quantidade de casas decimais. Um caso de uso é a quantidade de casas decimais do produto na Central de Notas.  
        * \*rm\_controle\*\*: Define o tipo de controle. Um caso de uso é o controle adicional de estoque do produto na Central de Notas.
      </td>
    </tr>

    <tr>
      <td>
        VALOR
      </td>

      <td>
        Valor da propriedade. Cada propriedade possui uma definição particular que pode variar de simples informações como “true/false” até informações complexas como querys, ou caminhos de classes e etc.
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).
      </td>
    </tr>

    <tr>
      <td>
        NUMOS
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>

    <tr>
      <td>
        LIBERADO
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>
  </tbody>
</Table>

## TDDINS

Contém informações relativas ao mapeamento de instâncias. A chave natural e única desta tabela é a **NOMEINSTANCIA**.

| Campo          | Descrição                                                                                              |
| :------------- | :----------------------------------------------------------------------------------------------------- |
| NUINSTANCIA    | Informação de controle interno. Utilizado como identificador único de registro.                        |
| NOMETAB        | Nome da tabela.                                                                                        |
| NOMEINSTANCIA  | Nome da instância.                                                                                     |
| DESCRINSTANCIA | Descrição da instância.                                                                                |
| RAIZ           | Define se a instância é a principal. Podemos criar uma instância filha de outra instância.             |
| ATIVO          | Define se a instância está ativa.                                                                      |
| EXPRESSAO      | Permite definir um critério que será usado como filtro na consulta.                                    |
| ADICIONAL      | Define se o campo é adicional. Usado para artefatos personalizados.                                    |
| RESOURCEID     | Define o identificador único de tela. Usado para criar lançador de tela, geralmente telas de cadastro. |
| CONTROLE       | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).                                   |
| NUMOS          | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.                      |
| LIBERADO       | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.                      |

## TDDLIG

Contém informações relativas ao mapeamento das ligações entre as instâncias. Este processo é usado para\
mapear FKs para se tornar um campo de pesquisa dentro das telas da plataforma.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Campo
      </th>

      <th>
        Descrição
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        TIPLIGACAO
      </td>

      <td>
        Define o tipo de ligação. Ligações LEFT JOIN são sempre NÃO obrigatórias. Porém é possível forçar que a ligação seja obrigatória através do campo OBRIGATORIA.  

        I - INNER JOIN\
        L - LEFT JOIN
      </td>
    </tr>

    <tr>
      <td>
        EXPRESSAO
      </td>

      <td>
        Utilizado para definir uma expressão de ligação entre origem e destino.  

        Deve ser uma expressão do tipo SQL.  Por exemplo:  

        Na ligação Parceiro>CabecalhoNotaModelo podemos definir para trazer apenas notas do tipo Z (TIPMOV = 'Z').  

        Também é utilizado para definir outras estruturas via @ref-param:  

        * \*show-on-ui\*\*: Define se a ligação será visível. Geralmente usado para que a aba não seja criada nas telas dynaform.  
        * \*description\*\*: Permite definir uma nova descrição para a ligação.  
        * \*force-one-to-one\*\*: Força uma ligação 1:1 entre duas instâncias.  
        * \*include-in-deep-copy\*\*: Determina a ligação deve ser copiada pela função de duplicar registro do dataset.  
        * \*merge-on-root\*\*: Permite manipular os dados de duas tabelas ligadas 1:1 como se fossem apenas uma. Por exemplo Parceiro->ComplementoParc.  
        * \*add.tables\*\*: Define uma tabela de ligação. Deve ser usado com link.expression.  
        * \*link.expression\*\*: Define a expressão de ligação.
      </td>
    </tr>

    <tr>
      <td>
        INSERIR
      </td>

      <td>
        Determina o CASCADE da ligação para INSERT. Ou seja, ao incluir o registro pai também existe a possibilidade de incluir o filho.
      </td>
    </tr>

    <tr>
      <td>
        ALTERAR
      </td>

      <td>
        Determina o CASCADE da ligação para UPDATE. Ou seja, na alteração do registro pai também existe a possibilidade de alterar o filho.
      </td>
    </tr>

    <tr>
      <td>
        EXCLUIR
      </td>

      <td>
        Determina o CASCADE da ligação para DELETE. Ou seja, ao excluir o registro pai também existe a possibilidade de excluir o filho.
      </td>
    </tr>

    <tr>
      <td>
        OBRIGATORIA
      </td>

      <td>
        Determina se a ligação é obrigatória. Por exemplo, na ligação CabecalhoNota->Parceiro existe essa obrigatoriedade porque o Parceiro é fundamental no lançamento de notas.
      </td>
    </tr>

    <tr>
      <td>
        CONDICAO
      </td>

      <td>
        Define uma expressão de ligação entre origem e destino. Deve ser uma expressão do tipo BeanShell.
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).
      </td>
    </tr>

    <tr>
      <td>
        NUMOS
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>

    <tr>
      <td>
        LIBERADO
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>
  </tbody>
</Table>

## TDDLGC

Contém informações relativas ao mapeamento dos campos de ligação entre as instâncias.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Campo
      </th>

      <th>
        Descrição
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUINSTORIG
      </td>

      <td>
        Informação de controle interno. Utilizado para ligação do campo de origem.
      </td>
    </tr>

    <tr>
      <td>
        NUCAMPOORIG
      </td>

      <td>
        Informação de controle interno. Utilizado para ligação do campo de origem.
      </td>
    </tr>

    <tr>
      <td>
        NUINSTDEST
      </td>

      <td>
        Informação de controle interno. Utilizado para ligação do campo de destino.
      </td>
    </tr>

    <tr>
      <td>
        NUCAMPODEST
      </td>

      <td>
        Informação de controle interno. Utilizado para ligação do campo de destino.
      </td>
    </tr>

    <tr>
      <td>
        ORIG\_OBRIGATORIA
      </td>

      <td>
        Define se o campo deve ser preenchido para completar a ligação. Por exemplo:  

        Na ligação de CabecalhoNota->OrdemCarga. Para vincular uma ordem de carga a nota é necessário informar também a empresa, pois a ligação completa é (CODEMP, ORDEMCARGA).
      </td>
    </tr>

    <tr>
      <td>
        ORDEM
      </td>

      <td>
        Campo obsoleto. Atualmente não está sendo utilizado para nenhuma funcionalidade.
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).
      </td>
    </tr>

    <tr>
      <td>
        NUMOS
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>

    <tr>
      <td>
        LIBERADO
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>
  </tbody>
</Table>

## TRDCON

Contém informações relativas aos controles de menu.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Campo
      </th>

      <th>
        Descrição
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUCONTROLE
      </td>

      <td>
        Informação de controle interno. Utilizado como identificador único de registro.
      </td>
    </tr>

    <tr>
      <td>
        DESCRCONTROLE
      </td>

      <td>
        Descrição do controle. Por exemplo, o nome da tela, o nome do item de menu.
      </td>
    </tr>

    <tr>
      <td>
        TIPOCONTROLE
      </td>

      <td>
        Define o tipo de controle.  

        *Controles usados:*\
        FB - Frame Builder\
        MN - Item de Menu\
        DS - Tela\
        PL - Painel  

        *Controles obsoletos:*\
        CA - Controle Abas\
        BT - Botão\
        GR - Grade\
        LK - Link\
        FS - Grupo (Field Set)\
        PG - Página\
        AB - Aba\
        CP - Campo\
        TV - Texo
      </td>
    </tr>

    <tr>
      <td>
        TIPOFILHOS
      </td>

      <td>
        Define o tipo de controle dos controles filhos. Possui as mesma opções de TIPOCONTROLE.
      </td>
    </tr>

    <tr>
      <td>
        ORIFILHOS
      </td>

      <td>
        Tipo de orientação dos controles filhos. Esta informação está obsoleta.  

        H - Horizontal\
        V - Vertical
      </td>
    </tr>

    <tr>
      <td>
        NOME
      </td>

      <td>
        Nome do controle. Deve ser um identificador único. No caso de telas, geralmente, usamos o mesmo valor do resourceID.
      </td>
    </tr>

    <tr>
      <td>
        ADICIONAL
      </td>

      <td>
        Define se o controle é adicional. Usado para artefatos personalizados.
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).
      </td>
    </tr>

    <tr>
      <td>
        NUMOS
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>

    <tr>
      <td>
        LIBERADO
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>
  </tbody>
</Table>

## TRDPCO

Contém informações relativas às propriedades dos controles.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Campo
      </th>

      <th>
        Descrição
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUCONTROLE
      </td>

      <td>
        Informação de controle interno. Utilizado como identificador único de registro.
      </td>
    </tr>

    <tr>
      <td>
        NOME
      </td>

      <td>
        Define o nome da propriedade. Existem diversas propriedades para funcionalidades diversas.  

        * \*resourceID\*\*: Define o identificador único de tela.  
        * \*resourceIDAcessos\*\*: Permite definir um resourceID exclusivo para controle de acessos. Quando informado, o resourceID não será utilizado para tal controle.  
        * \*entityName\*\*: Permite definir o nome da instância principal de uma determinada tela. Em telas dynaform esse atributo será utilizado para disponibilização de botões de ação e relatórios personalizados.  
        * \*contexto\*\*: Define o contexto da tela ou item de menu. Geralmente está relacionado ao módulo. Por exemplo: mge, mgecom, mgecontab, mgecot, mgectbz, mgefin.  
        * \*MI\_S4W8LB\*\*: Permite definir o código da licença necessária para uso da tela.  
        * \*paramMenuAtivo\*\*: Permite definir uma estrutura de verificação de parâmetro para ativar uma determinada tela.  
        * \*showMenu\*\*: Propriedade do tipo boolean que permite inativar um item de menu ou tela. Existem duas situações mais comuns:  
        * 1 - Telas descontinuadas.  
        * 2 - Telas que podem ser abertas apenas por outras telas.  
        * \*accessValidator\*\*: Permite definir um validador de acessos personalizado. Um caso de uso é a Central de Notas (CentralNotasAccessValidator).  
        * \*icon-info\*\*: Permite definir o caminho da imagem do módulo (framebuilder).  
        * \*onlyHtml5\*\*: Permite definir que determinada tela será aberta apenas no layout HTML5.  
        * \*hideCrudOperations\*\*: Propriedade do tipo booleana que permite desabilitar as configurações de acessos de CRUD na tela de Acessos. Um caso de uso é a tela Gerente On-Line - GOL.
      </td>
    </tr>

    <tr>
      <td>
        VALOR
      </td>

      <td>
        Define o valor da propriedade. Cada propriedade possui uma definição particular que pode variar de simples informações como “true/false” até informações complexas como querys, ou caminhos de classes e etc.
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).
      </td>
    </tr>

    <tr>
      <td>
        NUMOS
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>

    <tr>
      <td>
        LIBERADO
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>
  </tbody>
</Table>

## TRDFCO

Contém o mapeamento das ligações dos controles.

| Campo           | Descrição                                                                         |
| :-------------- | :-------------------------------------------------------------------------------- |
| NUCONTROLE      | Informação de controle interno. Utilizado como identificador único de registro.   |
| NUCONTROLEFILHO | Informação de controle interno. Utilizado como identificador único de registro.   |
| ORDEM           | Define a ordem do controle filho.                                                 |
| ATIVO           | Permite ativar ou inativar um controle filho.                                     |
| ADICIONAL       | Define se o controle é adicional. Usado para artefatos personalizados.            |
| CONTROLE        | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).              |
| NUMOS           | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |
| LIBERADO        | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |

## TRDEVE

Contém informações relativas aos eventos de controle.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Campo
      </th>

      <th>
        Descrição
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        NUCONTROLE
      </td>

      <td>
        Informação de controle interno. Utilizado como identificador único de registro.
      </td>
    </tr>

    <tr>
      <td>
        ONCLICK
      </td>

      <td>
        Permite definir o lançador da tela. Geralmente será um link no formato:  

        **Tela 100% dynaform:**\
        $\{dynaform:NomeDaInstancia}  

        Ex: $\{dynaform:Bairro}  

        **Demais telas:**\
        /contexto/NomeDaTela.xhtml5?mgeSession=$\{mge.session.id}\&resourceID=$\{resourceID}  

        Ex: /mgefin/MovimentacaoFinanceira.flex?mgeSession=$\{mge.session.id}\&resourceID=$\{resourceID}
      </td>
    </tr>

    <tr>
      <td>
        CONTROLE
      </td>

      <td>
        Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).
      </td>
    </tr>

    <tr>
      <td>
        NUMOS
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>

    <tr>
      <td>
        LIBERADO
      </td>

      <td>
        Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.
      </td>
    </tr>
  </tbody>
</Table>

## TDDIAC

Contém informações relativas aos acessos especiais de controle.

| Campo     | Descrição                                                                                                  |
| :-------- | :--------------------------------------------------------------------------------------------------------- |
| SEQUENCIA | Informação de controle interno.                                                                            |
| IDACESSO  | Define o identificador para validação do acesso. Neste caso, será o resourceID da tela.                    |
| SIGLA     | Define o identificador do acesso. Não pode repetir para o mesmo IDACESSO.                                  |
| DESCRICAO | Descrição do acesso. Essa informação será visualizada na tela de Acessos para a tela definida em IDACESSO. |
| CONTROLE  | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).                                       |
| NUMOS     | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.                          |
| LIBERADO  | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção.                          |

## TDDTABI18N

Internacionalização para a descrição das tabelas: TDDTAB.DESCRTAB

| Campo    | Descrição                                                                         |
| :------- | :-------------------------------------------------------------------------------- |
| NOMETAB  | Define o nome da tabela.                                                          |
| LOCALE   | Define o idioma.                                                                  |
| TEXTO    | Texto internacionalizado de acordo com o idioma definido (LOCALE).                |
| CONTROLE | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).              |
| NUMOS    | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |
| LIBERADO | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |

## TDDCAMI18N

Internacionalização para a descrição dos campos: TDDCAM.DESCRCAMPO

| Campo     | Descrição                                                                         |
| :-------- | :-------------------------------------------------------------------------------- |
| NOMETAB   | Define o nome da tabela.                                                          |
| NOMECAMPO | Define o nome do campo.                                                           |
| LOCALE    | Define o idioma.                                                                  |
| TEXTO     | Texto internacionalizado de acordo com o idioma definido (LOCALE).                |
| CONTROLE  | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).              |
| NUMOS     | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |
| LIBERADO  | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |

## TDDOPCI18N

Internacionalização para as opções de campo (TDDOPC.OPCAO)

| Campo     | Descrição                                                                         |
| :-------- | :-------------------------------------------------------------------------------- |
| NOMETAB   | Define o nome da tabela.                                                          |
| NOMECAMPO | Define o nome do campo.                                                           |
| VALOR     | Define o valor da opção.                                                          |
| LOCALE    | Define o idioma.                                                                  |
| TEXTO     | Texto internacionalizado de acordo com o idioma definido (LOCALE).                |
| CONTROLE  | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).              |
| NUMOS     | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |
| LIBERADO  | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |

## TDDINSI18N

Internacionalização para a descrição das instâncias (TDDINS.DESCRINSTANCIA)

| Campo         | Descrição                                                                         |
| :------------ | :-------------------------------------------------------------------------------- |
| NOMEINSTANCIA | Define o nome da instância                                                        |
| LOCALE        | Define o idioma.                                                                  |
| TEXTO         | Texto internacionalizado de acordo com o idioma definido (LOCALE).                |
| CONTROLE      | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).              |
| NUMOS         | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |
| LIBERADO      | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |

## TRDCONI18N

Internacionalização para a descrição dos controles (TRDCON.DESCRCONTROLE)

| Campo        | Descrição                                                                         |
| :----------- | :-------------------------------------------------------------------------------- |
| NOMECONTROLE | Define o nome do controle.                                                        |
| LOCALE       | Define o idioma.                                                                  |
| TEXTO        | Texto internacionalizado de acordo com o idioma definido (LOCALE).                |
| CONTROLE     | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).              |
| NUMOS        | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |
| LIBERADO     | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |

## TDDI18N

Internacionalização para abas, agrupadores de campo e qualquer outra situação não prevista nas demais tabelas de internacionalização.

| Campo    | Descrição                                                                         |
| :------- | :-------------------------------------------------------------------------------- |
| CHAVE    | Define o identificador único.                                                     |
| LOCALE   | Define o idioma.                                                                  |
| TEXTO    | Texto internacionalizado de acordo com o idioma definido (LOCALE).                |
| CONTROLE | Usado internamente pelo atualizador (WPM ou Gerenciador de pacotes).              |
| NUMOS    | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |
| LIBERADO | Campo obsoleto. Antigamente era usado para liberação dos artefatos para produção. |

## Consulta ao Dicionário de Dados

**Consulta com SGBD**

Para consultar o dicionário de dados diretamente pelo SGBD, use instruções SQL para recuperar informações sobre as tabelas e seus campos:

```sql
SELECT * FROM TDDTAB;
```

<Image title="SGBD.jpg" alt={831} align="center" border={true} src="https://files.readme.io/0f1b55e-SGBD.jpg">
  Consulta utilizando SGBD - SQL Developer
</Image>

**Consulta com DWFDesigner**

Para consultar o dicionário de dados pelo DWFDesigner, acesse Tabelas > Abrir Tabela... e pesquise pela tabela em questão.

<Image title="dwf_abrir_tabela.jpg" alt={581} align="center" width="smart" border={true} src="https://files.readme.io/b703fdc-dwf_abrir_tabela.jpg">
  Consulta pelo DWF Designer
</Image>

> 🚧 Atenção
>
> A alteração indevida de dados das tabelas do dicionário de dados pode comprometer a integridade e desempenho do banco de dados.

# Recursos avançados do Dicionário de dados

Confira neste [link](https://developer.sankhya.com.br/docs/recursos-avan%C3%A7ados) recursos avançados do dicionário de dados

## Como tirar dúvidas?

Para tirar dúvidas e compartilhar informações, use a sala [Dicionário de Dados](https://comunidade.sankhya.com.br/c/plataforma/dicionario-de-dados/47) da comunidade Sankhya Developer.