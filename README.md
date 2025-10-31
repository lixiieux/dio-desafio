# dio-desafio
# Projeto DIO: Gerenciando Instâncias EC2 na AWS

Este repositório documenta os conceitos aprendidos durante o **Módulo 2: Computação na Nuvem com EC2** do bootcamp Santander Code Girls 2025 - AWS Cloud Foundations, oferecido pela Digital Innovation One (DIO).

O objetivo deste projeto é consolidar o conhecimento sobre os principais serviços de computação e armazenamento da AWS, com foco no gerenciamento de instâncias EC2 e na criação de imagens AMI.

## ✒️ Módulos de Aprendizado

Com base nas aulas, os seguintes tópicos foram estudados:

1.  **Amazon EC2 (Elastic Compute Cloud)**
2.  **Armazenamento na Nuvem (EBS & S3)**
3.  **Gerenciamento de Instâncias EC2 (Foco em AMIs)**

---

## 1. Amazon EC2 (Elastic Compute Cloud)

O EC2 é o serviço central da AWS para computação. Ele permite alugar "servidores virtuais", conhecidos como **instâncias**, para executar aplicações. É um serviço IaaS (Infraestrutura como Serviço) que oferece controle total sobre o sistema operacional e os recursos de computação.

## 2. Armazenamento na Nuvem

Para suportar as instâncias EC2 e outras aplicações, o módulo abordou os principais serviços de armazenamento:

* **Amazon S3 (Simple Storage Service):** Um serviço de armazenamento de objetos altamente escalável. É usado para guardar arquivos, backups, e hospedar sites estáticos. Os dados são organizados em "buckets".
* **Amazon EBS (Elastic Block Store):** Funciona como o "disco rígido" (HD ou SSD) virtual para as instâncias EC2. É um armazenamento em bloco persistente usado para o sistema operacional e dados que precisam de acesso rápido pela instância.

## 3. Gerenciamento de Instâncias EC2 (com AMIs)

O gerenciamento eficaz de instâncias é crucial. O principal conceito estudado foi a **AMI (Amazon Machine Image)**.

### O que é uma AMI?

Uma AMI (Imagem de Máquina da Amazon) é uma imagem de máquina virtual pré-configurada. Ela funciona como um "template" ou "molde" para criar novas instâncias EC2.

Uma AMI inclui:
* O Sistema Operacional (ex: Linux, Windows).
* Servidores de aplicação (ex: Apache, Nginx).
* Aplicações e softwares instalados.

### Criação e Uso de AMIs

1.  **Criação:** As AMIs podem ser criadas a partir de instâncias EC2 que já estão em execução ou que foram paradas. Isso captura um "instantâneo" (snapshot) de todo o ambiente configurado.

2.  **AMIs Públicas e Privadas:**
    * **Públicas:** Fornecidas pela AWS (ex: Ubuntu, Amazon Linux) ou pela comunidade no Marketplace.
    * **Privadas:** AMIs que você cria e armazena na sua própria conta. São usadas para garantir segurança e manter suas personalizações.

3.  **Personalização:** A grande vantagem é poder iniciar uma instância EC2 "limpa" (pública), instalar todos os seus softwares, configurar definições de segurança e, em seguida, criar uma AMI privada a partir dela. Isso facilita a **replicação do ambiente** de forma rápida e padronizada.

4.  **Iniciar Instâncias:** Ao lançar uma nova instância EC2, você deve selecionar uma AMI. Ela fornece todas as informações necessárias para o boot, incluindo o volume do dispositivo raiz (root) e as permissões de inicialização.

---

## 4. Desafio Prático: Arquitetura S3 / EC2 / Lambda

Como parte prática do módulo, foi proposto o desafio de desenhar uma arquitetura básica na nuvem utilizando o [www.drawio.com](https://www.drawio.com/).

O objetivo foi conectar os serviços estudados (EC2, S3) com um serviço *serverless* (AWS Lambda) para demonstrar o fluxo de dados.

### Meu Diagrama de Arquitetura

Abaixo está o diagrama criado para solucionar o desafio, mostrando como um usuário pode interagir com o S3, que por sua vez pode acionar uma Lambda Function para processamento de dados e se comunicar com uma instância EC2.

*(**Instrução para você:** Coloque a imagem .png ou .jpg do seu diagrama aqui. Se você a colocou na pasta `images`, o código seria: `![Meu Diagrama](images/meu-diagrama.png)`)*

<img width="804" height="544" alt="image" src="https://github.com/user-attachments/assets/d29567fd-a498-4f36-8faf-1868b18daaa0" />


### Conceitos Aplicados no Diagrama

* **S3:** Usado como "porta de entrada" para o upload de arquivos (ex: fotos, dados).
* **AWS Lambda:** Uma função *serverless* que é acionada (triggered) automaticamente quando um novo objeto é colocado no bucket S3. Sua função é processar esse objeto (ex: redimensionar uma imagem, validar dados).
* **Amazon EC2:** A instância de servidor principal (back-end) que pode ser notificada pela Lambda ou consultar os dados processados para exibi-los em uma aplicação.
