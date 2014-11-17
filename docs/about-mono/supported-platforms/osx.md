---
title: OSX
redirect_from:
  - /Mono:OSX/
  - /Mono_on_MacOS_X/
---

Introdução ao Mono no MacOS X
-------------------------------

Mono suportou MacOS X desde a versão 10.3 (Panther) e suporta ambos, versões baseadas em intel e PowerPC com configurações suportadas em 32 e 64 bits

Você pode usar o Mono no OSX para construir aplicativos de servidor, console e GUI. Leia abaixo as opções disponíveis para o desenvolvimento de aplicações GUI.

Se você está interessado em criar aplicações GUI nativa, use o[MonoMac](/docs/tools+libraries/libraries/monomac/)
ligações e nossa MonoDevelop suplemento. Leia a descrição de [MonoMac](/docs/tools+libraries/libraries/monomac/) para mais informações sobre como começar.

Instalando Mono no MacOS X
--------------------------

Você pode usar Mono tanto como em tempo de execução para executar o aplicativo existente, ou como um SDK para desenvolver novas aplicações com Mono.

Visite o [página de download] (/download/) para encontrar o mais recente pacote de MacOS X. Execute-o e siga as instruções, você pode obter um tempo de execução de base, ou um tempo de execução completa, além de um kit de desenvolvimento de software.

Se você está pensando em desenvolver aplicações com Mono, sugerimos que você também [instalar o MonoDevelop IDE] (http://monodevelop.com/download) depois de instalar o Mono.

O pacote Mono inclui:

-   O Mono Runtime
-   GUI Toolkits: Windows.Forms and Gtk# for OSX.
    -  Nota: o [MonoMac](/docs/tools+libraries/libraries/monomac/) kit de ferramentas GUI para o desenvolvimento nativo OSX GUI é atualmente um download separado.
-  SDK: C #, Visual Basic compiladores, montadores e ferramentas
-  XSP servidor ASP.NET
-  Páginas de manual.

Este pacote instala como um quadro de /Library/Framework(da mesma maneira que os pacotes são instalados Java). Symlinks são criados para os executáveis em /usr/bin. Se você gostaria de acessar o mono *manpages* você vai ter que adicionar /Library/Frameworks/Mono.framework/Versions/Current/man para o seu *manpath*. O pacote MacOS X Mono não inclui [Gtk#](/GtkSharp), XSP ou mod_mono. These will have to be compiled from source.

Nossos pacotes atualmente requerem Mono OSX 10.4 ou melhor, para as versões mais antigas, você vai precisar para construir a partir do código fonte.

Usando Mono no MacOS X
---------------------

Neste ponto, você deve usar Mono partir da linha de comando, o conjunto usual de comandos que estão disponíveis em outros portos do Mono estão disponíveis.

Para construir aplicativos que você pode usar ["mcs"](/docs/about-mono/languages/csharp/), para executar, então você pode usar [mono](/docs/advanced/runtime/).

A partir de um shell de terminal, você pode experimentá-lo:

``` bash
$ vi hello.cs
$ mcs hello.cs
$ mono hello.exe
Hello, World
$
```

A maioria dos usuários estariam usando o [MonoDevelop IDE](http://monodevelop.com) para criar seus projetos.

Você terá a opção de [GUI toolkits](/docs/gui/gui-toolkits/) para a construção de sua aplicação, a partir de várias plataformas puro, a Mac-específica utilizando [MonoMac](/docs/tools+libraries/libraries/monomac/).

Suporte de 32 e 64 bits
---------------------

Os pacotes Mono publicados neste site fornecer uma Mono VM de 32 bits.

Suporte para VMs de 64 bits como de Mono 2.10 só está disponível se você construir Mono partir do código fonte e instalar sua própria cópia da VM. No futuro nós enviaremos mono e binários mono64 para nossos usuários.

O suporte de 64 bits tem algumas limitações hoje e é por isso que nós não inteiramente ligado a ele:

-  Nossa implementação Windows.Forms usa carbono e, como tal, não seria trabalhar com um 64-bit Mono.
-  MonoDevelop usa Carbon em sua integração de menu para que ele não seria executado em um 64-bit VM.
-  Ligações MonoMac não foram portados para 64 bits.

Apoio 64-bit Mono em toda a linha exigiria também nos de enviar um 64-bit Gtk + pilha e que iria aumentar o tamanho do download para a maioria dos usuários.

Fazendo aplicações clientes
----------------------------

Existem algumas opções para construir aplicações cliente no OSX, você deve escolher a tecnologia que melhor se adapta às suas metas, suas escolhas são:

||
|Conjunto de ferramentas | roda em Linux | Funciona em Windows | Roda em Mac | Estilo Binding | Licença | Status |
|[MonoMac](/docs/tools+libraries/libraries/monomac/)|não|não|sim|Fortemente tipado C # ligação a APIs Cacau | MIT X11 | desenvolvido ativamente, baseia-se nas aulas de design de [MonoTouch](http://monotouch.net) mas ainda incompleto. Esta será a nova ligação para o Mono no OSX padrão. download separado.|
|Gtk#|sim|sim|sim|Fortemente tipado C de ligação à plataforma cruzada Gtk + API #. Aplicações olhar estrangeiro sobre OSX |. LGPL v2 | desenvolvido ativamente, multiplataforma. Pacote com Mono.|
|Windows.Forms|sim|sim|sim|Aplicação multiplataforma de Windows.Forms da Microsoft. Aplicações olhar estrangeiro sobre OSX |. MIT X11 | A API Windows.Forms foi congelada no tempo pela Microsoft. Pacote com Mono.|
|[MonObjc](http://www.monobjc.net)|não|não|sim|A ligação com as APIs nativas do cacau, mas requer a utilização manual de seletores Objective-C para trabalhar com, envoltório relativamente fina em torno das APIs subjacentes |. LGPL v3 | desenvolvido ativamente. Download separado. |
| CocoaSharp | não | não | sim | Ligação às APIs nativas de cacau, mas requer a utilização manual de seletores de Objective-C para trabalhar com, envoltório relativamente fina em torno das APIs subjacentes |. MIT X11 | Não é mais desenvolvido, não é mantida, preterido . Pacote com Mono. |

Executando aplicações Mono no MacOS X
------------------------------------

A execução de aplicativos em MacOS X é muito semelhante a sistemas Linux, a partir do terminal:

    mono meuPrograma.exe

Para GTK # aplicações, é mais fácil de executá-los da mesma forma, mas usando *xterm* de X11.app

    A MacOS X lançador Mono específica estava em desenvolvimento, mas o seu estado não está claro hoje

Windows.Forms
-------------

Implementação de Mono da API System.Windows.Forms é construído em cima de carbono e só pode ser executado com Mono em sistemas de 32 bits. O olhar ea sensação de aplicações system.windows.forms imita o estilo do Windows e atualmente não tornar como uma aplicação nativa OSX.

Bibliotecas de Terceiros
---------------------

[ObjC#](/archived/objcsharp "ObjCSharp")é uma ponte de dois transparente forma que permite que o CLR para acessar os ricos quadros objectivec subjacentes, bem como proporcionar acesso directo aos quadros CLR da língua ObjectiveC.

Desinstalar o Mono no Mac OS X
-----------------------------

Execute este script em um terminal:

    #!/bin/sh -x

    #Este script remove Mono de um sistema OS X. Ele deve ser executado como root

    rm -r /Library/Frameworks/Mono.framework

    rm -r /Library/Receipts/MonoFramework-*

    for dir in /usr/bin /usr/share/man/man1 /usr/share/man/man3 /usr/share/man/man5; do
       (cd ${dir};
        for i in `ls -al | grep /Library/Frameworks/Mono.framework/ | awk '{print $9}'`; do
          rm ${i}
        done);
    done

