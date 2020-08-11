# SA3 - Vendedores
## SX3 - Campos da tabela

X3_ORDEM|X3_CAMPO|X3_TIPO|X3_TAMANHO|X3_DECIMAL|X3_TITULO|X3_DESCRIC|X3_PICTURE|X3_VALID|X3_RELACAO|X3_F3|X3_BROWSE|X3_VISUAL|X3_CONTEXT|X3_CBOX|X3_WHEN|
-|-|-|-:|-:|-|-|:-:|:-:|-|-|-|-|-|-|:-:|
01|A3_FILIAL|C|2|0|Filial|Filial do Sistema|||||N|||||
02|A3_COD|C|6|0|Codigo|Codigo do Vendedor|`@!` |`existchav("SA3")` |||S|||||
03|A3_NOME|C|40|0|Nome|Nome do Vendedor|||||S|||||
04|A3_NREDUZ|C|25|0|Nome Reduzid|Nome Reduzido do Vendedor|||||S|||||
05|A3_END|C|40|0|Endereco|Endereco do Vendedor|`@!` ||||S|||||
06|A3_BAIRRO|C|20|0|Bairro|Bairro do Vendedor|`@!` ||||S|||||
07|A3_MUN|C|15|0|Municipio|Municipio do Vendedor|`@!` ||||N|||||
08|A3_EST|C|2|0|Estado|Sigla da Federacao|`@!` |`ExistCpo("SX5","12"+M->A3_EST)` ||12|N|||||
09|A3_CEP|C|8|0|CEP|Cod Enderecamento Postal|`@R 99999-999` ||||N|||||
10|A3_DDDTEL|C|3|0|DDD|Código do DDD|`999` ||||N|A|R|||
11|A3_MSBLQL|C|1|0|Status|Status do Registro|`@!` |`Pertence("12")` |"2"|||A|R|1=Inativo;2=Ativo||
12|A3_TEL|C|15|0|Telefone|Numero do Telefone|`@R 999999999` ||||N|A|R|||
13|A3_FAX|C|15|0|FAX|Numero do FAX do vend.|`@!` ||||N|||||
14|A3_TELEX|C|10|0|Telex|Numero do Telex|`@!` ||||N|||||
15|A3_TIPO|C|1|0|Tipo|Tipo de Representante|`@!` ||||N|||I=Interno;E=Externo;P=Parceiro||
16|A3_CGC|C|14|0|CNPJ/CPF|CNPJ/CPF do vendedor|`@R 99.999.999/9999-99` |`Vazio() .OR. CGC(M->A3_CGC)` |||N|||||
17|A3_INSCR|C|18|0|Ins. Estad.|Inscricao Estadual|`@!` ||||N|||||
18|A3_INSCRM|C|18|0|Ins. Municip|Inscricao Municipal|`@!` ||||N|||||
19|A3_EMAIL|C|80|0|E-Mail|E-Mail|||||S|A|R|||
20|A3_HPAGE|C|30|0|Home-Page|Home-Page|||||S|||||
21|A3_CODUSR|C|6|0|Cod.Usuario|Código de Usuário|`@!` |`Vazio() .OR. ( UsrExist(M->A3_CODUSR) .AND. ExistChav("SA3",M->A3_CODUSR,7) )` ||USR|N|A|R||`!(ALTERA .AND. SuperGetMv("MV_LJTPCOM",,"1") == "3")` |
22|A3_SUPER|C|6|0|Supervisor|Nome do Supervisor Vendas||`vazio().or.(existcpo("SA3",M->A3_SUPER) .And. M->A3_SUPER != M->A3_COD .And. M->A3_SUPER != M->A3_GEREN )` ||SA3|N|||||
23|A3_GEREN|C|6|0|Gerente|Nome do Gerente de Vendas||`vazio().or.(existcpo("SA3",M->A3_GEREN) .And. M->A3_GEREN != M->A3_COD .And. M->A3_SUPER != M->A3_GEREN )` ||SA3|N|||||
24|A3_FORNECE|C|6|0|Fornecedor|Cód.Vend. como Fornecedor|`@!` |`vazio() .or. ExistCpo("SA2",M->A3_FORNECE)` ||FOR|N||||`M->A3_GERASE2=="S"` |
25|A3_LOJA|C|2|0|Loja|Loja Vend.como Fornecedor|`@!` |`Vazio() .Or. ExistCpo("SA2",M->A3_FORNECE+M->A3_LOJA)` |||N||||`M->A3_GERASE2=="S"` |
26|A3_GERASE2|C|1|0|Forma Pgto|Forma de pagamento|`@!` |`Pertence("SNF")` |||N|||S=Contas a Pagar;F=Folha de Pagamento;N=Sem interface||
27|A3_BCO1|C|3|0|Banco|Banco do Vendedor|`@!` |`ExistCpo("SA6")` ||BCO|N|||||
28|A3_REGIAO|C|3|0|Regiao|Regiao do Vendedor|`@!` ||||N|||||
29|A3_COMIS|N|5|2|Comissao|Comissao do Vendedor|`@E 99.99` ||||N|||||
30|A3_ALEMISS|N|3|0|% Pg na Emis|% pago n emissao|`999` |`A040ALIQ("B")` |||N|||||
31|A3_ALBAIXA|N|3|0|% Pg na Baix|% pago na baixa|`999` |`A040ALIQ("E")` |||N|||||
32|A3_ICM|C|1|0|Base c/ICMS|Comissao sobre ICM S/N ?|`@!` |`Pertence("SN")` |||N|||S=Sim;N=Nao||
33|A3_ICMSRET|C|1|0|B.c/ICM Ret.|Comissao sobre ICM Retido|`@!` |`Pertence("SN")` |||N|||S=Sim;N=Nao||
34|A3_UNIDAD|C|6|0|Unidade|Unidade do Vendedor|`@!` |`ExistCpo('ADK',M->A3_UNIDAD)` ||ADK||V|R|||
35|A3_ISS|C|1|0|Base c/ISS|Comissao sobre ISS S/N ?|`@!` |`Pertence("SN")` |||N|||S=Sim;N=Nao||
36|A3_DSCUNID|C|40|0|Nome|Nome da Unidade|`@!` ||IIF(!INCLUI,ALLTRIM(POSICIONE('ADK',1,XFILIAL('ADK')+SA3->A3_UNIDAD,'ADK_NOME')),'')|||V|V|||
37|A3_IPI|C|1|0|Base c/IPI|Comissao sobre IPI S/N ?|`@!` |`Pertence("SN")` |||N|||S=Sim;N=Nao||
38|A3_REGSLA|C|6|0|Registro SLA|Registro ID do SLA|`@!` |||||A|R|||
39|A3_QTCONTA|N|6|0|Qtd. Contas|Quant. de Contas do Vend.|`999999` |||||A|R|||
40|A3_GRPREP|C|6|0|Equipe|Equipe de Vendas|`@!` |`ExistCpo("ACA")` ||ACA||V||||
41|A3_FRETE|C|1|0|Base c/Frete|Comissao sobre Frete S/N?|`@!` |`Pertence("SN")` |||N|||S=Sim;N=Nao||
42|A3_DSCGRP|C|40|0|Nome|Nome da Equipe|`@!` ||IIF(!INCLUI,ALLTRIM(POSICIONE('ACA',1,XFILIAL('ACA')+SA3->A3_GRPREP,'ACA_DESCRI')),'')|||V|V|||
43|A3_ACREFIN|C|1|0|Acresc.Fin.|Considera Acresc.Financ.|`@!` |`Pertence("SN")` |"N"||N|||S=Sim;N=Nao||
44|A3_DIA|N|2|0|Dia Pgto Com|Dia de Pagto da comissao|`99` |`M->A3_DIA >= 1 .AND. M->A3_DIA <= 31` |||S|||||
45|A3_DDD|C|1|0|Dias da Cond|Dias(Mes)|`@!` |`Vazio() .or. pertence("F")` |||N|||F=Fora Mes||
46|A3_CARGO|C|6|0|Cargo|Cargo do Vendedor|`@!` |`Vazio().OR.ExistCpo('SUM')` ||SUM||A|R|||
47|A3_PERDESC|N|5|2|%Desc.Autori|% Desconto Autorizado|`@E 99.99` ||||N|||||
48|A3_TIPSUP|C|3|0|Tip.Superior|Tipo do Superior|`@!` |||||V|R|||
49|A3_DIARESE|N|3|0|Dias Reserva|Numero de dias de Reserva|`999` ||||N|||||
50|A3_SENHA|C|6|0|Senha|Senha do Vendedor|`@!` ||||N|||||
51|A3_PEDINI|C|6|0|Ped.Inicio|Pedido Inicial|`999999` |||||A||||
52|A3_PEDFIM|C|6|0|Ped.Fim|Pedido Final|`999999` |||||A||||
53|A3_CLIINI|C|6|0|Cli.Inicio|Cliente Inicial|`@!` |||||A||||
54|A3_CLIFIM|C|6|0|Cli.Fim|Cliente Final|`@!` |||||A||||
55|A3_PROXPED|C|6|0|Prox.Pedido|Proximo Pedido|`999999` ||||N|A||||
56|A3_PROXCLI|C|6|0|Prox.Cliente|Proximo Cliente|`@!` ||||N|A||||
57|A3_SINCTAF|C|1|0|Sinc.Tarefa|Sincroniza Tarefa|`@!` |`PERTENCE("SN")` |"S"||S|A|R|S=Sim;N=Nao||
58|A3_SINCAGE|C|1|0|Sinc.Agenda|Sincroniza Agenda|`@!` |`PERTENCE("SN")` |"S"||S|A|R|S=Sim;N=Nao||
59|A3_FAT_RH|C|2|0|Fator RH|Fator RH|`@!` ||||S|||||
60|A3_GRUPSAN|C|6|0|Grupo Sang.|Grupo Sanguineo|`@!` ||||S|||||
61|A3_SINCCON|C|1|0|Sinc.Contato|Sincroniza Contato|`@!` |`PERTENCE("SN")` |"S"||S|A|R|S=Sim;N=Nao||
62|A3_PERAGE|C|1|0|Periodo|Periodo de Sincronizacao|`@!` |`Pertence("ABCDEF")` |"A"||S|A|R|A=Dia Atual;B=1 semana;C=1 mes;D=3 meses;E=6 meses;F=1 ano||
63|A3_DEPEND|C|2|0|Nº Dependent|Numero de Dependente|`@!` ||||S|||||
64|A3_PEN_ALI|N|8|0|Pensao Alim.|Pensao Alimenticia|`@E 99999999` ||||S|||||
65|A3_PERTAF|C|1|0|Periodo|Periodo Sincronizacao|`@!` |`Pertence("ABCDEF")` |"A"||S|A|R|A=Dia Atual;B=1 semana;C=1 mes;D=3 meses;E=6 meses;F=1 ano||
66|A3_TIMEMIN|C|4|0|Tempo Sinc.|Tempo Sincronizacao|`@!` ||"30"||S|A|R|||
67|A3_TIPVEND|C|1|0|Tipo Vend.|Tipo Vendedor|`@!` ||||S|||1=Cooperativa;2=Funcionario;3=Corretora||
68|A3_USUCORP|C|30|0|Usuario|Usuario Corporativo|`@!` ||||S|A|R|||
69|A3_URLEXG|C|50|0|Url Exchange|Url Exchange|`@!` ||||N|V|R|||
70|A3_NUMRA|C|6|0|Funcionário|Código do funcionário|`@!` |`ExistCpo("SRA")` ||SRA|N|A|R||`M->A3_GERASE2=="F"` |
71|A3_PAIS|C|3|0|País|País do vendedor|`@!` |`Vazio() .or. ExistCpo('SYA',M->A3_PAIS)` ||SYA|N|A|R|||
72|A3_DDI|C|6|0|DDI|DDI do vendedor|`999999` |`IIF(!EMPTY(M->A3_DDI), ExistCpo('ACJ',M->A3_DDI),.T.)` ||ACJ|N|A|R|||
73|A3_HABSINC|C|1|0|Habil.Sinc.|Habilita Sincronizacao|`@!` |`PERTENCE("SN")` |||N|A|R|S=Sim;N=Nao||
74|A3_CEL|C|15|0|Celular|Celular do vendedor||||||A|R|||
75|A3_ADMISS|D|8|0|Admissao|Data Admissão|`99/99/99` |||||||||
76|A3_NVLSTR|C|30|0|Nivel Estr.|Nivel de acesso na estr.|`@!` ||||N|V|R|||
77|A3_NIVEL|N|2|0|Nivel Estr.|Nivel estrutura de vendas|`99` ||||N|V|R|||
78|A3_LANEXG|C|5|0|Idioma Exch.|Idioma Exchange|`@!` ||||N|A|R|pt_BR=Português (Brasileiro);en_US=Inglês (Estados Unidos)"||
79|A3_PISCOF|C|1|0|Abt. Imp.Com|Abate impostos da comis.|`9` |`Pertence("1234")` ||||||1=Nao;2=PIS;3=COFINS;4=Ambos||
80|A3_BIAGEND|C|1|0|Imp Age Exc|Importa agenda Exchange|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Não||
81|A3_BICONT|C|1|0|Imp Cont Exc|Importa Contatos Exchange|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Não||
82|A3_BITAREF|C|1|0|Imp Tar Exc|Importa Tarefas exchange|`@!` |`Pertence("12")` |"2"||N|A|R|1=Sim;2=Não||
83|A3_EMACORP|C|100|0|Email|Email Corporativo|`@!` ||||S|A|R|||
84|A3_DTUMOV|D|8|0|Data Umov.me|Data Transf. UMov.me|||||N|A|R|||
85|A3_CODISS|C|6|0|Cod.Aliq.ISS|Codigo Aliquota SS|`@!` |`Vazio() .Or. ExistCpo('FIM',M->A3_CODISS)` ||FIM|N|A|R||`M->A3_GERASE2=='S'` |
86|A3_HREXPO|C|8|0|Hr. Ult. Exp|Hora da última Exportação|||||N|V|R|||
87|A3_HRUMOV|C|5|0|Hora Umov.me|Hora Transf. Umov.me|||||N|A|R|||
88|A3_FILFUN|C|2|0|Filial Func|Filial Funcionario|||||N|V|R|||
89|A3_BASEIR|C|1|0|Base c/Irf|Base com Irrf|`@!` |`Pertence('12')` |"1"||N|A|R|1=Nao;2=Sim||
90|A3_MSEXP|C|8|0|Ident.Exp.|Ident.Exp.Dados|||||N|V|R|||
91|A3_MODTRF|C|1|0|Mod.Transf.|Modo de Transferencia|`@!` |`Pertence("123")  .AND. IIF(FindFunction("A040ValSup"),A040ValSup(M->A3_MODTRF),.T.)` |"3"|||A|R|1=Transferência Direta;2=Transferência p/ Solicitacao;3=Não Transfere||
92|A3_SNAEXG|C|100|0|Senha EXG|Senha do Exchange|`@!` |||||V|R|||
93|A3_USERLGA|C|17|0|Log de Alter|Log de Alteração|||||N|V|R|||
94|A3_USERLGI|C|17|0|Log de Inclu|Log de Inclusão|||||N|V|R|||
95|A3_HAND|C|1|0|HandHeld|Usa HandHeld?|`9` |`Pertence('12')` |'2'|||A|R|1=Sim;2=Não||


## SIX - Índices da tabela

ORDEM|CHAVE|DESCRICAO|F3|NICKNAME|SHOWPESQ|
-|-|-|-|-|-|
1|A3_FILIAL+A3_COD|Codigo|||S|
2|A3_FILIAL+A3_NOME|Nome|||S|
3|A3_FILIAL+A3_CGC|CNPJ/CPF|||S|
4|A3_FILIAL+A3_GEREN|Gerente|||S|
5|A3_FILIAL+A3_SUPER|Supervisor|||S|
6|A3_FILIAL+A3_GRPREP|Equipe|ACA||S|
7|A3_FILIAL+A3_CODUSR|Cod.Usuario|||S|
8|A3_FILIAL+A3_NVLSTR|Nivel Estr.|||N|


