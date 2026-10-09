# Laboratório de Redes -- Cisco Packet Tracer

Laboratório desenvolvido durante meus estudos de **Redes de
Computadores**, utilizando o **Cisco Packet Tracer**.

O objetivo foi praticar a configuração de redes IPv4, comunicação entre
redes diferentes e roteamento estático utilizando roteadores Cisco.

## Topologia

## 🖥️ Topologia

![Topologia da rede](topologia.png)

A topologia é composta por:

-   3 roteadores
-   4 switches
-   Diversos computadores
-   Diferentes redes IPv4
-   Enlaces entre roteadores utilizando redes distintas

Fluxo principal:

``` text
PC → Switch → Roteador → Roteador → Roteador → Switch → PC
```

## Conceitos praticados

-   Endereçamento IPv4
-   Máscara de sub-rede
-   Default Gateway
-   Configuração de interfaces de roteadores
-   Comunicação entre diferentes redes
-   Roteamento estático
-   Próximo salto (Next Hop)
-   Tabela de roteamento
-   Testes de conectividade com `ping`
-   Análise do caminho com `tracert`
-   Verificação de rotas com `show ip route`
-   Verificação de interfaces com `show ip interface brief`

## Configuração de roteamento estático

Foi utilizado o comando:

``` cisco
ip route <rede-de-destino> <máscara> <próximo-salto>
```

Exemplo utilizado no laboratório:

``` cisco
ip route 192.168.6.0 255.255.255.0 192.168.5.2
```

Nesse caso:

-   **Rede de destino:** `192.168.6.0/24`
-   **Próximo salto:** `192.168.5.2`
-   O endereço `192.168.5.2` corresponde à interface do próximo roteador
    no caminho.

## Comandos utilizados

### Verificar a tabela de roteamento

``` cisco
show ip route
```

### Verificar as interfaces

``` cisco
show ip interface brief
```

### Testar conectividade

``` text
ping 192.168.6.2
```

### Verificar o caminho até um destino

``` text
tracert 192.168.6.2
```

## Principal aprendizado

O laboratório ajudou a entender que um roteador precisa conhecer o
caminho até redes que não estão diretamente conectadas.

Em uma rota estática, o endereço informado como **next hop** é o
endereço do **próximo roteador**, e não necessariamente o endereço do
computador de destino.

Exemplo:

``` text
PC12
192.168.3.3
   ↓
R3
192.168.3.1
   ↓
192.168.5.1 ─── 192.168.5.2
                    ↓
                   R4
                    ↓
              192.168.6.0/24
                    ↓
                 PC13
              192.168.6.2
```

Para que o R3 alcance a rede do PC13:

``` cisco
ip route 192.168.6.0 255.255.255.0 192.168.5.2
```

## Ferramenta

**Cisco Packet Tracer**

Este laboratório faz parte dos meus estudos práticos de **Redes de
Computadores**.
