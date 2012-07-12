# Testes de performance

Os testes de performance serão feitos a partir de uma máquina virtual, pois ela já foi configurada para possibilitar a abertura de muitos *file descriptors*.

## Máquina virtual

Esta máquina possui o ``httperf`` instalado e as modificações necessárias para que ele execute testes com alto grau de concorrência.

Para utilizar a máquina, é necessário usar o [vagrant] (http://vagrantup.com/).

### Setup

Basta adicionar uma cópia da máquina virtual ao Vagrant. Para ter acesso a esta cópia entre em contato com o líder técnico do seu time.

```sh
$ vagrant box add benchmark benchmark.box
```

Em seguida, a VM já pode ser iniciada e acessada via ssh:

```sh
$ vagrant up # Inicia a VM
$ vagrant ssh # Conecta-se a VM por ssh
vagrant@lucid32:~$ cd /vagrant/ # Os arquivos do projeto se encontram neste diretório 
```

### Teardown

Para desligar a VM, basta utilizar o seguinte comando:

```sh
$ vagrant halt
```

## Execução dos testes

Para execução dos testes, é utilizado o gem [stresser](https://github.com/guiocavalcanti/stresser). Este gem utiliza-se do [HTTPerf](http://www.hpl.hp.com/research/linux/httperf/) para gerar os gráficos a partir das informações coletadas pelo HTTPerf.


### Setup

Crie um ``.conf`` com as configurações necessárias para o teste como em [sample](https://github.com/redu/benchmarks/blob/master/sample.conf).

### Execução

Para executar o teste, basta fazer uma chamada ao ``stresser``, passar o arquivo de configuração e o path onde os resultados deverão ser alocados.

```sh
$ bundle exec stresser -c sample.conf -o result.csv
```

Em seguida, o próprio ``stresser`` dará as instruções para a geração dos gráficos.

## Referências

1. [Vagrant](http://vagrantup.com/)
2. [Fork do stresser](https://github.com/guiocavalcanti/stresser)
3. ``man httperf`` ou [PDF](http://www.hpl.hp.com/research/linux/httperf/httperf-man-0.9.pdf)
4. [httperf: A Tool for Measuring Web Server Performance](http://www.hpl.hp.com/research/linux/httperf/wisp98/httperf.pdf)
5. Configurações necessárias a VM: http://posidev.com/blog/2009/06/04/set-ulimit-parameters-on-ubuntu/
6. Como aumentar o tamanho dos cookies no HTTPerf para funcionar com Rails: https://github.com/Gregg/httperf_big_cookies/commit/fbb2820c6de087a88d1724f49f72ad4aadb2c3d9
