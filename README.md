<p align="center">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" width="120" alt="Java Logo">
</p>

# 🖨️ Impressora Térmica Java

Projeto desenvolvido em **Java** com o objetivo de demonstrar a comunicação entre uma aplicação Java e uma impressora térmica utilizando conexão **TCP/IP**. O exemplo mostra como enviar comandos diretamente para a impressora por meio de um `Socket` e um `OutputStream`.

## 📷 Demonstração

<p align="center">
  <img src="https://github.com/user-attachments/assets/dc8223be-169a-45eb-ab66-1b61c87922ab"
       alt="Configuração da Impressora"
       width="700">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/0e3a90dd-75b6-48d8-aa20-12285489d5c4"
       alt="Exemplo de Impressão"
       width="700">
</p>



---

## ✨ Recursos

- Conexão com a impressora via endereço IP
- Impressão de textos
- Impressão da data e hora atuais
- Alteração do tamanho da fonte
- Alinhamento do texto
- Impressão em negrito
- Avanço do papel
- Corte automático
- Fechamento da conexão com a impressora

---

## 💻 Tecnologias

- Java
- Socket TCP/IP
- OutputStream

---

# 🔌 Conectando à impressora

```java
Socket impressora = new Socket("10.26.49.39", 9100);
OutputStream saida = impressora.getOutputStream();
```

---

# 🚀 Inicializando a impressora

```java
saida.write(new byte[] {0x1B, 0x40});
```

---

# 📅 Imprimindo data e hora

```java
LocalDateTime agora = LocalDateTime.now();
DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");

String datahora = "Data: " + agora.format(formato) + "\n\n";

saida.write(datahora.getBytes("CP850"));
```

---

# 🔠 Alterando o tamanho da fonte

Fonte ampliada:

```java
saida.write(new byte[] {0x1D, 0x21, 0x11});
```

Retornar ao tamanho padrão:

```java
saida.write(new byte[] {0x1D, 0x21, 0x00});
```

---

# 📍 Alinhando o texto

Centralizado

```java
saida.write(new byte[] {0x1B, 0x61, 0x01});
```

À esquerda

```java
saida.write(new byte[] {0x1B, 0x61, 0x00});
```

À direita

```java
saida.write(new byte[] {0x1B, 0x61, 0x02});
```

---

# 📝 Impressão em negrito

Ativar:

```java
saida.write(new byte[] {0x1B, 0x45, 0x01});
```

Desativar:

```java
saida.write(new byte[] {0x1B, 0x45, 0x00});
```

---

# 🖨️ Imprimindo texto

```java
saida.write("HELLO WORD!\n\n".getBytes("CP850"));

saida.write("SENAC - Tatuapé\n".getBytes("CP850"));

saida.write("Nathalia\n\n".getBytes("CP850"));
```

---

# 📄 Avançando o papel

```java
saida.write(new byte[] {0x1B, 0x64, 0x05});
```

---

# ✂️ Corte automático

```java
saida.write(new byte[] {0x1D, 0x56, 0x00});
```

---

# ✅ Finalizando a impressão

```java
saida.flush();
impressora.close();
```

---

# 📌 Exemplo completo

```java
Socket impressora = new Socket("10.26.49.39", 9100);
OutputStream saida = impressora.getOutputStream();

saida.write(new byte[] {0x1B, 0x40});

LocalDateTime agora = LocalDateTime.now();
DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");

String datahora = "Data: " + agora.format(formato) + "\n\n";

saida.write(datahora.getBytes("CP850"));

saida.write(new byte[] {0x1D, 0x21, 0x11});
saida.write(new byte[] {0x1B, 0x61, 0x01});

saida.write("HELLO WORD!\n\n".getBytes("CP850"));

saida.write(new byte[] {0x1D, 0x21, 0x00});
saida.write(new byte[] {0x1B, 0x61, 0x00});

saida.write(new byte[] {0x1B, 0x45, 0x01});
saida.write("SENAC - Tatuapé\n".getBytes("CP850"));

saida.write(new byte[] {0x1B, 0x45, 0x00});
saida.write("Nathalia\n\n".getBytes("CP850"));

saida.write(new byte[] {0x1B, 0x64, 0x05});
saida.write(new byte[] {0x1D, 0x56, 0x00});

saida.flush();
impressora.close();
```

---

## ⚙️ Requisitos

- Java
- Impressora térmica conectada à rede
- Endereço IP da impressora
- Porta TCP da impressora (9100)

---

## ▶️ Como executar

Clone o repositório:

```bash
git clone https://github.com/nathaliaarosario/Java.git
```

Acesse a pasta do projeto:

```bash
cd Java/impressora_termica/src
```

Compile:

```bash
javac impressora/Impressora.java
```

Execute:

```bash
java impressora.Impressora
```

---

# 👩‍💻 Autor

**Nathalia Alves Rosário**

- GitHub: https://github.com/nathaliaarosario

---

# 📄 Licença

![GitHub License](https://img.shields.io/github/license/nathaliaarosario/Impressoura-Termica)


---
