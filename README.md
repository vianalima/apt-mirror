# apt-mirror-docker

<p align="center">
    <a href="https://travis-ci.com/flavienbwk/apt-mirror-docker.svg?branch=master" target="_blank">
        <img src="https://travis-ci.com/flavienbwk/apt-mirror-docker.svg?branch=master"/>
    </a>
</p>
<p align="center">Script apt-mirror atualizado, containerizado para espelhamento + serviço.</p>

Este repositório combina as atualizações de https://travis-ci.com/flavienbwk/apt-mirror-docker do (infelizmente) não mantido [repositório apt-mirror](https://github.com/apt-mirror/apt-mirror).

<p align="center">Status: testado e funcionando :heavy_check_mark:</p>

## Para saber

Um espelho de arquivo do Ubuntu pode **[atualizar a cada 6 horas](https://wiki.ubuntu.com/Mirrors)** (4 vezes ao dia, dependendo do fuso horário da localização do espelho). Para evitar uma sincronização ruim, inicie a sincronização do seu espelho cerca de 15 minutos após a meia-noite, 6h, meio-dia ou 18h (considerando o fuso horário do espelho).

Isso significa que seu tempo de download não deve exceder 6 horas para estar seguro: é por isso que recomendo usar [um provedor de nuvem](https://scaleway.com) para o download e, em seguida, recuperá-lo com `rsync`, por exemplo.

## Download e atualização

1. Edite o arquivo `mirror.list` à sua conveniência.

2. Execute o container `mirror`:

    ```bash
    docker-compose build
    docker-compose up mirror
    ```

> Este repositório é enviado com o `mirror.list`.

## Servindo

1. Verifique se seu espelhamento foi bem-sucedido em `./mirror/mirror/*` ou digitando `du -sh ./mirror`.

    Espera-se que você baixe cerca de **186.6 Gb** de arquivos no momento da escrita.

2. Execute o servidor:

    ```bash
    docker-compose up -d server
    ```

    O servidor será executado em [`localhost:8080`](http://localhost:8080).  

:point_right: Fique à vontade para adicionar um proxy reverso ou atualizar o [arquivo de configuração do nginx](./nginx.conf) para proteger o espelho com SSL/TLS.  
:point_right: Fique à vontade para enviar **pull requests** também!
