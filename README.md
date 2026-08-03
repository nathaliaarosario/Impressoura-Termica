# Impressora Térmica Java

Projeto desenvolvido em **Java** para comunicação com impressoras térmicas compatíveis com o protocolo **ESC/POS**, permitindo imprimir textos, avançar papel e realizar o corte automático ao final da impressão.

## Funcionalidades

- Impressão de texto
- Impressão de QR Code (quando suportado)
- Impressão de imagens
- Impressão de códigos de barras
- Avanço de papel
- Corte automático
- Envio de comandos ESC/POS
- Compatível com diversas impressoras térmicas

## Tecnologias

- Java
- ESC/POS
- Java Print Service

## Estrutura do Projeto

```
src/
├── Main.java
├── PrinterService.java
└── ...
```

---

# Exemplo de Impressão

```java
PrinterService printer = new PrinterService();

printer.println("================================");
printer.println("      CUPOM DE TESTE");
printer.println("================================");
printer.println("Produto A             R$ 10,00");
printer.println("Produto B             R$ 20,00");
printer.println("--------------------------------");
printer.println("TOTAL                 R$ 30,00");

printer.feed(4);
printer.cut();

printer.close();
```

---

# Imprimindo um texto simples

```java
PrinterService printer = new PrinterService();

printer.println("Olá Mundo!");

printer.feed(3);

printer.close();
```

---

# Avançando o papel

```java
printer.feed(5);
```

Equivalente ao comando ESC/POS:

```java
outputStream.write(new byte[]{
    0x1B,
    0x64,
    0x05
});
```

---

# Corte automático

```java
printer.cut();
```

Comando ESC/POS:

```java
outputStream.write(new byte[]{
    0x1D,
    0x56,
    0x00
});
```

---

# Corte parcial

```java
outputStream.write(new byte[]{
    0x1D,
    0x56,
    0x01
});
```

---

# Impressão utilizando OutputStream

```java
OutputStream out = printer.getOutputStream();

out.write("Impressão de teste\n".getBytes());

out.write(new byte[]{
    0x1B,
    0x64,
    0x05
});

out.write(new byte[]{
    0x1D,
    0x56,
    0x00
});

out.flush();
out.close();
```

---

# Exemplo de Cupom

```text
================================
          MERCADO TESTE
================================
Produto A             R$ 10,00
Produto B             R$ 20,00
Produto C             R$ 30,00
--------------------------------
TOTAL                 R$ 60,00

Obrigado pela preferência!
```

---

# Impressão de QR Code

```java
printer.printQRCode("https://github.com/nathaliaarosario");
```

---

# Impressão de Código de Barras

```java
printer.printBarcode("7891234567890");
```

---

# Compatibilidade

Este projeto pode ser utilizado com impressoras térmicas compatíveis com ESC/POS, incluindo:

- Epson
- Elgin
- Bematech
- Daruma
- Control iD
- POS-58
- POS-80
- XPrinter
- Outras impressoras ESC/POS

---

# Requisitos

- Java 17 ou superior
- Driver da impressora instalado
- Impressora compatível com ESC/POS

---

# Como executar

Clone o repositório:

```bash
git clone https://github.com/nathaliaarosario/Java.git
```

Entre na pasta:

```bash
cd Java/impressora_termica
```

Compile:

```bash
javac Main.java
```

Execute:

```bash
java Main
```

---

# Autor

Desenvolvido por **Nathalia Alves Rosário**

GitHub:
https://github.com/nathaliaarosario

LinkedIn:
https://www.linkedin.com/in/nathalia-alves-ros%C3%A1rio-01a5a2360/

---

# Licença
![GitHub License](https://img.shields.io/github/license/nathaliaarosario/Impressoura-Termica)

Este projeto está licenciado sob a licença MIT.
