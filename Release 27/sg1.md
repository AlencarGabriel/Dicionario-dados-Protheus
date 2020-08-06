# SG1 - Estruturas dos Produtos
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|G1_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
02|G1_COD|C|15|0|Código|Código do Produto|`@!` |`existcpo("SB1")` ||SB1|S|||||
03|G1_COMP|C|15|0|Componente|Código do componente|`@!` |`NaoVazio().And.ExistCpo("SB1").And.if(ModType(nModulo)=="I", AVA200comp() .and.AVA200desc(),A200Comp().And.A200Desc())` ||SB1|S|||||
04|G1_DESC|C|30|0|Descrição|Descrição do Componente|`@!` ||IF(!INCLUI,IF(!EMPTY(SG1->G1_COMP),POSICIONE('SB1',1,XFILIAL('SB1')+SG1->G1_COMP,'B1_DESC'),''),'')||N|V|V|||
05|G1_TRT|C|3|0|Sequência|Sequência|`@!` ||||S|||||
06|G1_QUANT|N|12|6|Quantidade|Quantidade|`@E 99999.999999` |`NaoVazio().And.If(ModType(nModulo)=="I",AVMA200QUANT(M->G1_QUANT,M->G1_COMP),MA200Quant(M->G1_QUANT,M->G1_COMP))` |||S|||||
07|G1_PERDA|N|5|2|Índice Perda|Índice de perda|`@E 99.99` |`Positivo()` |||S|||||
08|G1_INI|D|8|0|DT Inicial|Data Inicial da Validade||`NaoVazio()` |ddatabase||N|||||
09|G1_FIM|D|8|0|DT Final|Data Final da Validade||`NaoVazio() .And. M->G1_FIM >= M->G1_INI` |CTOD("31/12/49")||N|||||
10|G1_OBSERV|C|45|0|Observação|Observação do Produto|`@!` ||||N|||||
11|G1_FIXVAR|C|1|0|Qtd. Fix/Var|Qtde. Estr. Fixa/Variável|`@!` |`Pertence(" VF")` |"V"||N|||V=Variavel;F=Fixa||
12|G1_GROPC|C|3|0|Grupo Opcio.|Grupo de Opcionais|`@!` |`Vazio() .Or. ExistCpo("SGA")` ||SGAPCP|N|||||
13|G1_OPC|C|4|0|Item Opcion.|Item do Gr. de Opcionais|`@!` |`IF(!Empty(M->G1_GROPC),NaoVazio().And.ExistCpo("SGA",M->G1_GROPC+M->G1_OPC),Vazio())` |||N|||||
14|G1_REVINI|C|3|0|Rev. Inicial|Revis. Inicial Componente|`@!` ||||N|||||
15|G1_REVFIM|C|3|0|Rev. Final|Revis. Final Componente|`@!` ||"ZZZ"||N|||||
16|G1_NIV|C|2|0|Nível|Nível do produto|`99` ||||N|||||
17|G1_NIVINV|C|2|0|Nível Invert|Nível Invertido|`99` ||||N|||||
18|G1_POTENCI|N|6|2|Potência|Potência de Lote|`@E 999.99` |`A200Potenc()` |||S|||||
19|G1_OK|C|4|0|Ok|Substituir Componentes|||||N|||||
20|G1_TIPVEC|C|6|0|Tipo vetor|Tipo vetor||`VAZIO().OR.EXISTCPO("SX5","VC"+M->G1_TIPVEC)` ||VC|N|A|R|||
21|G1_VECTOR|C|6|0|Vetor|Vetor||`VAZIO().OR.EXISTCPO("SHV",M->G1_TIPVEC+M->G1_VECTOR,1)` |||N|A|R|||
22|G1_VLCOMPE|C|1|0|Vl.Com.Perda|Valor comercial a perda|`@!` |`Pertence(" SN")` |"N"||N|A|R|S=Sim;N=Nao||
23|G1_USAALT|C|1|0|Usa Altern.?|Usa Alternativo?|`@!` |`Pertence("12")` |"1"||N|A|R|1=Sim;2=Não||
24|G1_LOCCONS|C|2|0|Armazém|Armazém de consumo|`@!` |`vazio() .or. ExistCpo("NNR")` ||NNR|S|A|R|||
25|G1_FANTASM|C|1|0|Fantasma?|Componente Fantasma?||`vazio() .or. Pertence("12")` |||S|A|R|1=Sim;2=Não||
26|G1_LISTA|C|10|0|Lista|Lista de componente|`@!` ||||S|A|R|||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|G1_FILIAL+G1_COD+G1_COMP+G1_TRT|Código + Componente + Sequência|SB1+SB1||S|
2|G1_FILIAL+G1_COMP+G1_COD|Componente + Código|SB1+SB1||S|
3|G1_FILIAL+G1_COD+G1_GROPC+G1_OPC|Código + Grupo Opcio. + Item Opcion.|||S|
4|G1_FILIAL+G1_TIPVEC+G1_VECTOR|Tipo vetor + Vetor|||S|
5|G1_FILIAL+G1_COD+DTOS(G1_FIM)+G1_TRT|Código + DT Final + Sequência|||S|


