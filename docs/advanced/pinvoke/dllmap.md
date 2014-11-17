---
title: DllMaps
redirect_from:
  - /Config_DllMap/
  - /DllMap/
---

Visão global
--------

DllMaps são usados para mapear nomes de biblioteca do Windows (.dll) para linux nomes de biblioteca / unix (usually .so).

DllMaps são especificado em qualquer arquivo de configuração mono, ou em arquivos de configuração de montagem.

O \ <dllmap \> é uma directiva que pode ser usado diretamente no diretório \ <configuration \> seção.

### Crianças

O \<dllmap\> directiva pode ser ainda mais sintonizado com a \<dllentry\> directiva.

O \<dllentry\> directiva pode ser utilizado para mapear um par dll/function específica para uma biblioteca diferente e também um nome de função diferente. Ele deve aparecer dentro de um elemento dllmap apenas com o atributo dll especificada.

O elemento DLLENTRY leva três atributos:

-   dll: Esta é a biblioteca de destino, onde a função pode ser encontrado.

-   name: Este é o nome como a função de como ele aparece nos metadados: é o nome do método P/Invoke.

-   target: Este é o nome da função para pesquisa, em vez do nome especificado no método P/Invoke.

Uso
-----

Você usar a diretiva dllmap para mapear bibliotecas compartilhadas referenciados por P/Invoke nas vossas assembléias para uma biblioteca compartilhada diferente.

Isso normalmente é usado para mapear as bibliotecas do Windows para nomes de biblioteca Unix. O elemento dllmap leva dois atributos:

-   dll: Esta deve ser a mesma corda usada no atributo DllImport. Isso pode ser prefixado com **i:** para especificar que o nome correspondente deve ser feito de uma forma case-insensitive.
-   target: Este deve ser o nome da biblioteca onde a função pode ser encontrado: este nome deve ser adequado para uso com o nativo plataforma partilhada rotinas de biblioteca de carregamento(dlopen etc.).

Note-se que as entradas posteriores irão substituir as entradas definidas no início do arquivo.

Em Mono libera após 1.1.18, ambos os elementos dllmap e DLLEntry permitir que as duas seguintes atributos que a tornam fácil de usar um único arquivo de configuração e suporte a vários sistemas operacionais e arquiteturas com diferentes requisitos de mapeamento:

-   **os**: Este é o nome do sistema operacional para o qual o mapeamento deve ser aplicada. Os valores permitidos são: linux, osx, solaris, FreeBSD, OpenBSD, NetBSD, Windows, AIX, HPUX.
-   **cpu** Este é o nome da arquitectura para o qual o mapeamento deve ser aplicada. Os valores permitidos são: x86, x86-64, SPARC, ppc, s390, s390x, braço, mips, alpha, hppa, ia64.
-   **wordsize** você pode usar isso para diferenciar entre 32 e sistemas de 64 bits. Os valores possíveis são: 32 e 64.

O valor de atributo para ambos os atributos pode ser uma lista de valores permitidos, separados por vírgulas. Além disso, o primeiro caractere pode ser um '!' para inverter o sentido. Um valor de atributo de "! Janelas, osx", por exemplo, significa que a entrada é considerado em todos os sistemas operacionais, exceto no Windows e OS X.

Não são permitidos espaços em qualquer parte do valor.

Exemplo
=======

O exemplo a seguir mapeia as referências ao \`cygwin1.dll' shared library to the \`libc.so.6' arquivo:

``` xml
    <configuration>
            <dllmap dll="cygwin1.dll" target="libc.so.6"/>
    </configuration>
```

Este mapeia o seguinte método C#:

``` csharp
    [DllImport ("libc")]
    static extern void somefunction ();
```

Para uma função diferente em libdifferent.so, mas para a mesma função na biblioteca **libanother.so** quando rodando sob os sistemas operacionais Solaris e FreeBSD.

``` xml
    <configuration>
        <dllmap dll="libc">
            <dllentry dll="libdifferent.so" name="somefunction" target="differentfunction" />
            <dllentry os="solaris,freebsd" dll="libanother.so" name="somefunction" target="differentfunction" />
        </dllmap>
    </configuration>
```

Problemas comuns
---------------

-   [DllNotFoundException](/docs/advanced/pinvoke/dllnotfoundexception/)


