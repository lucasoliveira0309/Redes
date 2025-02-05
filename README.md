!Modo exec previlegiado
enable
    !Configuração da data e hora
    clock set 19:30:00 04 February 2025
    !modo de configuração global
    configure terminal
        !configuração do hostname
        hostname sw-01
        !serviço de senhas
        service password-encryption
        !serviço de marcação de data e hora 
        service timestamps log datetime msec
        !desativar a resolução de nomes
        no ip domain-lookup 
        !baner da mensagem do dia 
        banner motd #AVISO: CUIDADO!#
        !segurança do modo enable
        enable secret 123@senac
        !Criando Usuários e senhas de acesso
        username senac secret 123@senac 
        username lucas password 123@senac
        username admin privilege 15 secret 123@senac
        !Configurar a Linha (Line) Console
        line console 0
        !Forçar Login Local
        login Local
        !Forçar senha do Console
        password 123@senac
        !Sicronismo de Log
        logging synchronus 
        !tempo de inatividade
        exec-timeout 5 30 
        !sair de todos os modos
        end
        !salvar as configurações
        copy running-config startup-config
    !salvar as configurações da RAM para VRAM
    copy running-config startup-config
!sair do modo enable
disable

enable  
    !visualizando as configurações 
    show running-config


............................................................................................................................................

enable
    configure terminal
    !Configurar as linhas virtuais 
    line vty 0 4 
            login local
            password 123@senac
            logging synchronous
            exec-timeout 5 30 
