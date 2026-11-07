# Calculadora Baseada em Texto em C

Calculadora de terminal em C com menu interativo. O usuário escolhe uma operação (adição, subtração, multiplicação ou divisão), informa dois números e recebe o resultado na hora, podendo repetir quantas vezes quiser.

![Status](https://img.shields.io/badge/status-concluído-brightgreen)
![Linguagem](https://img.shields.io/badge/linguagem-C-A8B9CC)
![Licença](https://img.shields.io/badge/licença-MIT-blue)

## 📖 Sobre

Projeto de [estudo / trabalho da faculdade] para praticar os fundamentos de C: entrada e saída, estruturas de controle, funções e, principalmente, **validação de entrada**. O foco foi fazer um programa que não quebra com entradas inesperadas, como letras no lugar de números, opções fora do menu ou divisão por zero.

## ✨ Funcionalidades

- Menu com quatro operações (adição, subtração, multiplicação e divisão) e opção de sair
- Aceita números **inteiros e decimais**
- Validação da opção do menu (inteiro de 1 a 5) com nova tentativa em caso de erro
- Validação dos números digitados, repetindo a pergunta se a entrada for inválida
- Tratamento de **divisão por zero** com mensagem de erro
- Pergunta se o usuário quer realizar outra operação, aceitando `s` ou `n` (maiúsculo ou minúsculo)
- Encerramento limpo quando a entrada acaba (Ctrl+D / Ctrl+Z)

## 🛠️ Tecnologias

- C (padrão C99 ou superior)
- GCC
- Bibliotecas padrão: `stdio.h`, `stdlib.h`, `string.h`, `ctype.h`

## 📂 Estrutura do projeto

```
calculadora-c/
├── calculadora.c
├── .gitignore
├── LICENSE
└── README.md
```

## 🚀 Como executar

**Pré-requisitos:** GCC instalado (Linux, macOS, ou Windows via MinGW/WSL).

```bash
# 1. Clone o repositório
git clone https://github.com/SEU-USUARIO/calculadora-c.git
cd calculadora-c

# 2. Compile
gcc -Wall -Wextra -o calculadora calculadora.c

# 3. Execute
./calculadora        # Linux/macOS/WSL
calculadora.exe      # Windows
```

> **Windows:** se os acentos aparecerem estranhos no terminal, rode `chcp 65001` antes de executar.

## 💡 Exemplo de uso

```
===============================
   Calculadora Simples
===============================
Selecione uma operação:
1. Adição
2. Subtração
3. Multiplicação
4. Divisão
5. Sair
Opção: 1
Digite o primeiro número: 5
Digite o segundo número: 3
Resultado: 5 + 3 = 8
Deseja realizar outra operação? (s/n): s

===============================
   Calculadora Simples
===============================
...
Opção: 4
Digite o primeiro número: 10
Digite o segundo número: 0
Erro: Divisão por zero não é permitida.
Deseja realizar outra operação? (s/n): n
Obrigado por usar a calculadora! Até a próxima.
```

## 🧪 Testes

O projeto não usa framework de testes. A verificação foi feita manualmente, e também dá para automatizar um caso simples passando a entrada por pipe:

```bash
printf '1\n5\n3\nn\n' | ./calculadora
```

Casos verificados:

| Cenário | Entrada | Resultado esperado |
|---|---|---|
| Adição com inteiros | `1`, `5`, `3` | `Resultado: 5 + 3 = 8` |
| Números decimais | `3`, `2.5`, `4` | `Resultado: 2.5 * 4 = 10` |
| Divisão por zero | `4`, `10`, `0` | `Erro: Divisão por zero não é permitida.` |
| Opção fora do intervalo | `9` | Mensagem de erro e nova solicitação |
| Opção não numérica | `abc` | Mensagem de erro e nova solicitação |
| Número inválido | `12abc` | Mensagem de erro e nova solicitação |
| Resposta inválida em s/n | `talvez` | Pede que digite `s` ou `n` |
| Resposta em maiúsculo | `S` / `N` | Aceita normalmente |
| Sair pelo menu | `5` | Mensagem de despedida e encerramento |

## ⚠️ Limitações

- Os resultados são impressos com `%g`, que mostra até 6 dígitos significativos (por exemplo, `1 / 3` aparece como `0.333333`).
- Valores do tipo `double` têm a imprecisão usual de ponto flutuante.
- A limpeza de tela entre operações (opcional no enunciado) não foi implementada, para manter o código portável entre sistemas.

## 🧠 O que aprendi

- **Por que usar `fgets` + `strtol`/`strtod` em vez de `scanf`:** ler a linha inteira e converter depois evita que lixo no buffer de entrada cause loops infinitos, e permite detectar entradas como `12abc`.
- **Modularização:** separar menu, leitura de opção, leitura de números e confirmação em funções deixou o `main` curto e fácil de seguir.
- **Casos de borda:** divisão por zero, fim de entrada (EOF) e respostas em maiúsculo exigiram pensar além do "caminho feliz".

## 🗺️ Próximos passos

- [ ] Adicionar operações como potência, resto e raiz quadrada
- [ ] Guardar um histórico das operações da sessão
- [ ] Escrever testes automatizados e um `Makefile`

## 🎓 Contexto acadêmico

- **Enunciado:** exercício "Calculadora Baseada em Texto em C", com requisitos de menu e validação, operações matemáticas e loop de múltiplas operações.

## 📄 Licença

Distribuído sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👤 Autor

**Luidger Gomes Gonzaga**
[LinkedIn](https://linkedin.com/in/luidger-gomes-2228859b/) · [E-mail](mail to:gomesgonzaga@gmail.com)
