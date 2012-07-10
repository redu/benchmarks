# Testes de performance

## Setup

### HTTPerf

-  Mac: ``$ brew install httpef``
- Linux: ``$ sudo apt-get install httperf``
- Windows: WHAT!?

## Rodando testes

- Crie um ``.conf`` no formato aceito pelo [HTTPerf](http://www.hpl.hp.com/research/linux/httperf/) e execute o comando ``bundle exec stresser``. O Gem [stresser][https://github.com/moviepilot/stresser] é utilizado como auxiliar para gerar gráficos a partir do resultado do HTTPerf.

## Referências



1. ``man httperf`` ou [PDF](http://www.hpl.hp.com/research/linux/httperf/httperf-man-0.9.pdf)
2. [httperf: A Tool for Measuring Web Server Performance](http://www.hpl.hp.com/research/linux/httperf/wisp98/httperf.pdf)

