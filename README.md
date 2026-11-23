# 🖨️ Controle de Impressora Térmica Elgin i8/i9 em C

## 📘 Descrição

Projeto desenvolvido em linguagem C para controlar uma impressora térmica Elgin i8 ou i9 por meio da biblioteca `E1_Impressora01.dll`.

O programa possui sistema de login, menu interativo e funções para configurar a conexão com a impressora, imprimir textos, QR Codes, códigos de barras e documentos fiscais SAT, além de abrir a gaveta de dinheiro e emitir sinais sonoros.

O trabalho foi desenvolvido para a disciplina de Programação em C. Todo o código-fonte do programa está concentrado no arquivo `main.c`.

## ✅ Funcionalidades

- Login com usuário e senha, permitindo até 3 tentativas.
- Menu interativo com 11 opções e opção 0 para sair.
- Configuração da conexão com a impressora.
- Abertura e fechamento da conexão.
- Fechamento automático da conexão ao encerrar o programa.
- Impressão de textos com quantidade de cópias definida pelo usuário.
- Impressão de QR Code com conteúdo digitado.
- Impressão de código de barras no padrão CODE 128.
- Impressão de cupom SAT utilizando o arquivo `XMLSAT.xml`.
- Impressão de cancelamento SAT utilizando o arquivo `CANC_SAT.xml`.
- Abertura da gaveta de dinheiro por dois comandos diferentes.
- Emissão de sinal sonoro com quantidade de apitos escolhida pelo usuário.
- Bloqueio das operações de impressão quando a conexão está fechada.
- Verificação dos retornos dos comandos da impressora, com mensagens de sucesso ou erro.
- Liberação da memória utilizada na leitura dos arquivos XML por meio de `free()`.
- Tratamento de entradas numéricas inválidas, evitando problemas quando o usuário digita letras.

## 🔑 Login de teste

| Usuário | Senha |
|---|---|
| `admin` | `1234` |

## 📁 Arquivos do projeto

```text
Trabalho_C_Impressora/
│
├── main.c
├── README.md
├── E1_Impressora01.dll
├── XMLSAT.xml
└── CANC_SAT.xml
```

**Descrição dos arquivos:**

- `main.c`: código-fonte principal do programa.
- `README.md`: documentação do projeto.
- `E1_Impressora01.dll`: biblioteca utilizada para comunicação com a impressora Elgin.
- `XMLSAT.xml`: arquivo de teste para impressão de cupom SAT.
- `CANC_SAT.xml`: arquivo de teste para impressão de cancelamento SAT.

A DLL correta e os dois arquivos XML devem estar disponíveis na raiz do projeto. O programa também precisa ser executado com a pasta do projeto como diretório de trabalho, pois os arquivos XML são acessados por caminhos relativos.

## ⚠️ Compatibilidade da DLL (32 ou 64 bits)

A arquitetura da DLL precisa ser compatível com a arquitetura do compilador utilizado.

Para verificar a arquitetura do GCC, execute no terminal:

```bash
gcc -dumpmachine
```

| Resultado | Arquitetura | DLL necessária |
|---|---|---|
| `x86_64-w64-mingw32` | 64 bits | x64 |
| `mingw32` | 32 bits | x86 |
| `i686-w64-mingw32` | 32 bits | x86 |

Copie a versão correspondente da `E1_Impressora01.dll` para a raiz do projeto.

## ⚙️ Como compilar e executar

**Requisitos:**

- Sistema operacional Windows.
- Compilador GCC compatível com Windows, como MinGW.
- DLL `E1_Impressora01.dll` na arquitetura correta.
- Arquivos XML disponibilizados junto ao projeto.

**Pelo terminal (GCC):**

1. Abra o terminal.
2. Acesse a pasta do projeto.
3. Execute os comandos:

```bash
gcc -std=c99 -Wall -Wextra main.c -o impressora.exe
```

4. Execute o programa:

```bash
impressora.exe
```

**Pelo Code::Blocks:**

1. Crie um projeto do tipo Console Application, selecionando a linguagem C.
2. Substitua o conteúdo do arquivo `main.c` pelo código deste projeto.
3. Coloque a DLL e os dois arquivos XML na pasta do projeto.
4. Em `Project → Properties → Build targets`, confira se o campo `Execution working dir` aponta para a pasta do projeto.
5. Compile e execute o programa.

## 🖥️ Como utilizar

1. Execute o programa.
2. Informe o usuário `admin` e a senha `1234`.
3. Escolha a opção `1` para configurar a conexão.
4. Para uma conexão USB, utilize os seguintes parâmetros:
   - Tipo: `1`
   - Modelo: `i8` ou `i9`
   - Conexão: `USB`
   - Parâmetro adicional: `0`
5. Escolha a opção `2` para abrir a conexão.
6. Após a confirmação da conexão, escolha a operação desejada no menu.
7. Para encerrar, escolha a opção `0`. Se a conexão estiver aberta, o programa tentará fechá-la automaticamente.

**Observação:** os parâmetros apresentados são os valores de referência para conexão USB indicados no material do trabalho. Outras formas de conexão dependem da configuração correspondente e do equipamento utilizado.

## 📋 Opções do menu

| Nº | Funcionalidade |
|---|---|
| 1 | Configurar conexão |
| 2 | Abrir conexão |
| 3 | Fechar conexão |
| 4 | Imprimir texto |
| 5 | Imprimir QR Code |
| 6 | Imprimir código de barras |
| 7 | Imprimir XML SAT |
| 8 | Imprimir XML de cancelamento SAT |
| 9 | Abrir gaveta (Elgin) |
| 10 | Abrir gaveta |
| 11 | Emitir sinal sonoro |
| 0 | Sair do programa |

## 🛠️ Problemas comuns

| Mensagem ou erro | Possível causa |
|---|---|
| Erro 126 ao carregar a DLL | DLL não localizada no diretório de execução ou alguma dependência necessária não encontrada. |
| Erro 193 ao carregar a DLL | Incompatibilidade entre a arquitetura da DLL e a do compilador (32 ou 64 bits). |
| Comando não encontrado na DLL | Biblioteca incorreta ou versão diferente da disponibilizada para o trabalho. |
| Erro ao abrir a conexão | Impressora desligada, cabo desconectado ou parâmetros de conexão incorretos. |
| Arquivo XML não encontrado | XML ausente ou programa executado com diretório de trabalho incorreto. |

## 👤 Autor

- IGOR BASILIO DE SOUZA HUDSON

## 📚 Referência

Biblioteca e documentação de comandos da impressora Elgin:

https://elgindevelopercommunity.github.io/group___m1.html