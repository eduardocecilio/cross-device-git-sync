## **Aplicação e Fluxo de Trabalho**

Este repositório descreve o processo para configurar um fluxo de trabalho eficiente utilizando o **Git** entre dois computadores (Mac e Windows) conectados ao **OneDrive**, com o objetivo de manter um repositório compartilhado entre as duas máquinas. O repositório está configurado para utilizar **SSH** como método de autenticação com o GitHub.

### **Objetivo**

O objetivo deste fluxo de trabalho é permitir que você possa trabalhar de forma sincronizada em dois computadores distintos, mantendo o código sempre atualizado sem a necessidade de realizar **git pull** em cada máquina após o **git push** de outra. Isso é possível porque as alterações feitas no OneDrive são sincronizadas automaticamente entre os computadores, e o Git apenas gerencia o versionamento do código.

### **Como Funciona**

1. **Ambiente Configurado**:
   - Dois computadores (um Mac e um Windows) possuem a mesma pasta de repositório Git armazenada no OneDrive, sendo automaticamente sincronizada entre as máquinas.
   - O repositório Git no OneDrive é configurado para usar autenticação **SSH** para o GitHub, e a chave SSH está configurada em ambos os computadores.
   
2. **Sincronização Automática**:
   - Quando um código é alterado em uma das máquinas, o arquivo é salvo automaticamente na pasta do OneDrive.
   - Após realizar as alterações, é feito um **commit** e **push** no GitHub em uma das máquinas.
   - Na segunda máquina, o código é automaticamente atualizado, pois o OneDrive mantém a pasta sincronizada. O Git detecta a alteração como um novo arquivo modificado e é possível realizar um **commit** e **push** sem a necessidade de executar **git pull**.

3. **Problemas Resolvidos**:
   - O fluxo evita a necessidade de estar sempre dando **git pull** quando alterna entre as duas máquinas, devido à sincronização do OneDrive.
   - As alterações feitas em um computador são automaticamente refletidas no outro, sem a interferência de conflitos de merge, desde que o processo de **commit** e **push** seja seguido corretamente.

### **Instruções de Uso**

Esses são os passos para configurar a estrutura entre os dois computadores, desde a instalação do Git até a sincronização automática:

1. **Configuração do Git**:
   - Certifique-se de ter o Git instalado nas duas máquinas.
   - Configure seu nome de usuário e email no Git com os seguintes comandos:
     ```bash
     git config --global user.name "Seu Nome"
     git config --global user.email "seuemail@example.com"
     ```

2. **Configuração do Repositório no OneDrive**:
   - Crie uma pasta no OneDrive que será usada para armazenar o repositório Git.
   - Inicie o repositório Git nessa pasta usando o comando `git init`.
   - Adicione o repositório remoto (GitHub) usando:
     ```bash
     git remote add origin git@github.com:seunome/repositorio.git
     ```

3. **Uso de SSH para GitHub**:
   - Gere uma chave SSH para cada máquina e adicione as chaves no GitHub para autenticação.
   - No GitHub, vá em "Settings" > "SSH and GPG keys" e adicione sua chave pública de cada máquina.

4. **Sincronização entre as Máquinas**:
   - Sempre que você fizer alterações em uma máquina, faça o **commit** e o **push** para o GitHub.
   - A segunda máquina irá automaticamente receber as atualizações através do OneDrive, e você pode fazer o **commit** e **push** da mesma forma.

5. **Resolução de Problemas Comuns**:
   - Certifique-se de que as mudanças feitas não gerem conflitos de merge. Caso ocorra algum conflito, resolva-o utilizando o Git.

### **Vantagens**

- **Facilidade de uso**: Não há necessidade de realizar **git pull** sempre que alternar entre os computadores.
- **Sincronização automática**: O OneDrive garante que os arquivos estejam sempre atualizados.
- **Versionamento com Git**: O fluxo de trabalho mantém o versionamento do código e o histórico de mudanças, sem afetar a sincronização entre as máquinas.

### 1. **Preparação do Ambiente**
   - **OneDrive**:
     - Certifique-se de que o OneDrive esteja instalado e sincronizado corretamente em ambos os computadores. A pasta onde o repositório Git será mantido deve estar completamente sincronizada entre os dois dispositivos.
     - **Possível erro**: Se a sincronização do OneDrive não for concluída corretamente, o repositório pode não ser atualizado entre os computadores. Certifique-se de que todos os arquivos estejam sincronizados antes de realizar operações no Git.

   - **Instalação do Git**:
     - Se o Git não estiver instalado no seu sistema, baixe e instale a versão mais recente [aqui](https://git-scm.com/). No Mac, é recomendado usar o Homebrew (`brew install git`).
     - **Possível erro**: Erros de configuração de chave SSH ou credenciais podem ocorrer se o Git não estiver configurado corretamente. Use `git config --global user.name "Seu Nome"` e `git config --global user.email "seuemail@dominio.com"` para configurar suas credenciais corretamente.

   - **VS Code**:
     - Para facilitar a edição do código, instale o VS Code em ambos os dispositivos. No Mac, use o Homebrew (`brew install --cask visual-studio-code`).
     - **Possível erro**: Certifique-se de que os plugins Git no VS Code estejam configurados corretamente para evitar problemas com as operações de commit e push.

### 2. **Configuração do Repositório Git**
   - **Criação do Repositório**:
     - Após instalar o Git, crie ou clone um repositório no OneDrive que será compartilhado entre os computadores.
     - **Possível erro**: Se o repositório for criado em uma pasta não sincronizada, as alterações feitas em um computador não serão refletidas no outro. Verifique se a pasta do repositório está corretamente no OneDrive e sincronizada.

### 3. **Gerenciamento de Arquivos com Git**
   - **Arquivos Ignorados**:
     - É importante adicionar um arquivo `.gitignore` ao seu repositório para garantir que arquivos desnecessários não sejam versionados. Isso pode incluir arquivos do sistema como `.DS_Store` (Mac) ou `Thumbs.db` (Windows).
     - **Possível erro**: Se o `.gitignore` não for configurado corretamente, o Git pode começar a rastrear arquivos indesejados. Além disso, verifique os finais de linha ao editar esse arquivo, pois pode causar conflitos (ex: `^M` no final de cada linha devido à diferença de sistemas operacionais).

### 4. **Sincronização e Resolução de Conflitos**
   - **Sincronização entre os Computadores**:
     - Ao trabalhar entre os computadores, sempre faça `git pull` para garantir que as alterações mais recentes sejam puxadas para o repositório local. Após isso, realize os commits e pushes para manter ambos os repositórios atualizados.
     - **Possível erro**: Se você esquecer de fazer `git pull` antes de fazer o commit, pode haver divergências entre os repositórios locais. O Git irá alertar para isso e você precisará resolver o conflito.

   - **Resolvendo Conflitos**:
     - Se ocorrerem conflitos durante o `git pull`, o Git irá indicá-los. Você deve abrir os arquivos conflitantes e decidir quais mudanças manter.
     - Após resolver os conflitos, use `git add <arquivo>` e `git commit` para concluir a resolução.
     - **Possível erro**: Se você não resolver os conflitos corretamente, os arquivos podem ser sobrescritos incorretamente ou o repositório pode acabar em um estado inconsistente.

### 5. **Uso de SSH para GitHub**
   - **Chave SSH**:
     - Para facilitar a autenticação com o GitHub, é recomendável usar chaves SSH em vez de senhas. Certifique-se de gerar a chave SSH no terminal (use `ssh-keygen -t rsa -b 4096 -C "seuemail@dominio.com"`) e adicionar a chave pública no GitHub.
     - **Possível erro**: Se a chave SSH não for configurada corretamente, o Git não conseguirá autenticar com o GitHub. Verifique se a chave está corretamente adicionada no `ssh-agent` e configurada no GitHub.

### 6. **Configuração de Final de Linha no Git**
   - **Evitar Problemas de Final de Linha**:
     - Se você usar Git em sistemas diferentes (Windows e Mac), pode ocorrer o problema de finais de linha diferentes (`\r\n` no Windows e `\n` no Mac). Isso pode ser resolvido configurando o Git para tratar esses finais de linha corretamente:
       ```bash
       git config --global core.autocrlf input  # No Mac
       git config --global core.autocrlf true   # No Windows
       ```
     - **Possível erro**: Se os finais de linha não forem tratados corretamente, você pode acabar com conflitos no código, onde as edições feitas em um computador são interpretadas como alterações no final de linha, mesmo que o conteúdo do arquivo não tenha sido alterado.
Esse processo de sincronização entre dois computadores utilizando o Git, o VS Code e o OneDrive foi criado para exemplificar uma maneira prática de compartilhar e atualizar código em tempo real entre diferentes dispositivos. Utilizando essas ferramentas, conseguimos garantir que as alterações feitas em um computador sejam refletidas no outro de maneira eficiente, sem conflitos, desde que as configurações sejam feitas corretamente.

No entanto, vale ressaltar que o uso do **VS Code** e do **OneDrive** foi uma escolha pessoal para facilitar a edição e o armazenamento dos arquivos. Outras ferramentas de edição de código, como **Sublime Text**, **Atom**, **IntelliJ**, ou **Vim**, podem ser usadas no lugar do VS Code, desde que o Git esteja configurado corretamente.

Além disso, embora o **OneDrive** tenha sido escolhido como sistema de armazenamento na nuvem para esse processo, outras plataformas de nuvem, como **Google Drive**, **Dropbox**, ou **iCloud**, também podem ser utilizadas, desde que ofereçam a capacidade de sincronização entre múltiplos dispositivos de maneira confiável e que seja possivel baixar esses apps em sua maquina, pois é necessario ter acesso a pasta locamente no computador.

Quanto aos pacotes e comandos específicos utilizados (como o `dos2unix`, o gerenciamento de final de linha e as configurações do Git), eles foram aplicados para resolver questões práticas que surgiram durante o processo, mas outras soluções podem ser viáveis, dependendo das necessidades e preferências de quem utilizar o repositório.

Este repositório serve como um exemplo e base para quem deseja implementar uma solução semelhante, mas estamos sempre abertos a sugestões e melhorias para adaptar o processo a diferentes contextos e necessidades de desenvolvimento. Sinta-se à vontade para contribuir com melhorias ou adaptar conforme o seu fluxo de trabalho!
