## PyNFe

![status](https://img.shields.io/badge/status-stable-green.svg) ![https://github.com/TadaSoftware/PyNFe/actions](https://github.com/TadaSoftware/PyNFe/workflows/PyNFe%20CI/badge.svg?branch=master) ![pyversions](https://img.shields.io/badge/python-3.6%20%7C%203.7%20%7C%203.8%20%7C%203.9%20%7C%203.10-blue)


Biblioteca de interface com os webservices de Nota Fiscal Eletrônica (NF-e) e Nota Fiscal de Consumidor Eletrônica (NFC-e) da SEFAZ e Receita Federal do Brasil, Nota Fiscal de Serviço Eletrônica (NFS-e) para Prefeituras e Manifesto de Documentos Fiscais Eletrônicos (MDF-e).

- **NF-e** visa substituir as notas fiscais séries 1 e 1A.
- **NFC-e** visa substituir as notas fiscais modelo 2 e cupom fiscal emitido por ECF.
- **NFS-e** padrão Abrasf para autorizadores Ginfes e Betha.
- **MDF-e** no padrão nacional deverá ser emitido obrigatoriamente no transporte de mercadoria intermunicipais por empresas prestadoras de serviço de transporte ou pelas demais empresas cujo transporte seja realizado em veículos próprios, arrendados ou transportador autônomo.


Características
------------

* NF-e e NFCe:
    * Atualizado para a versão 4.00
    * Modelo de Documento fiscal 55 e 65
    * Configuração para utilização em ambiente de produção e homologação (testes)
    * Emissão de notas fiscais normal e em contingência
    * Consulta Status do Serviço
    * Consultar Cadastro de contribuiente
    * Consultar nota fiscal pela chave de acesso
    * Consultar protocolo
    * Evento de cancelamento de notas
    * Evento de carta de correção
    * Evento de inutilizar de notas
    * Evento de manifestação do destinatário
    * Consultar Distribuição DF-e

* NFS-e:
    * Emissão de nota fiscal de serviço eletrônico
    * Consultar pelo número da NFS-e
    * Consultar por RPS (recibo provisório de serviço)
    * Consultar Lote
    * Cancelar NFS-e

* MDF-e:
    * Atualizado para a versão 3.00
    * Modelo de Documento 58
    * Emissão de Manifesto
    * Consultar Status do Serviço
    * Consultar MDF-e pela chave de acesso
    * Consultar MDF-es não encerrados
    * Consultar Recibo
    * Evento de Cancelamento
    * Evento de Encerramento de viagem
    * Evento de Inclusão de Condutor
    * Evento de Inclusão de DF-e
    * Evento de Pagamento DF-e

Dependências
------------

- lxml
  - Biblioteca de leitura e gravação de arquivos XML, de alta performance e fácil de implementar.
- signxml
  - Assinatura e validação do XML
- pyopenssl
  - Biblioteca para manuseio do certificado digital
- requests
  - Biblioteca para a comunicação com os webservices da SEFAZ
- suds-jurko (*apenas para NFS-e)
  - Biblioteca para a comunicação com os webservices via wsdl
- pyxb (*apenas para NFS-e)
  - Biblioteca para geração de bindings a partir de XML Schema(xsd)

Referências
-----------

- Sites oficiais:
  - NFe: http://www.nfe.fazenda.gov.br/
  - MDF-e: https://dfe-portal.svrs.rs.gov.br/mdfe

- lxml
  - http://lxml.de/

- requests
  - http://docs.python-requests.org/en/latest/
  - https://github.com/psf/requests
  - https://pypi.python.org/pypi/requests

- Schemas para validação dos arquivos
  - NFe: http://www.nfe.fazenda.gov.br/portal/listaConteudo.aspx?tipoConteudo=BMPFMBoln3w=
  - MDFe: https://dfe-portal.svrs.rs.gov.br/Mdfe/Documentos

- Validador de XML
  - NFe: https://www.sefaz.rs.gov.br/NFE/NFE-VAL.aspx
  - MDFe: https://dfe-portal.svrs.rs.gov.br/MDFE/ValidadorXML

- Validador de assinaturas
  - https://servicos.receita.fazenda.gov.br/servicos/assinadoc/ValidadorAssinaturas.app/valida.aspx

Instalação
-----------

```sh
pip3 install --user https://github.com/TadaSoftware/PyNFe/archive/master.zip
```

Opcional para NFS-e:

```sh
pip3 install --user -r https://github.com/TadaSoftware/PyNFe/raw/master/requirements-nfse.txt
```

Exemplos de uso
-----------
  - Consulta Status

```python
from pynfe.processamento.comunicacao import ComunicacaoSefaz

certificado = "/home/user/certificado.pfx"
senha = 'senha'
uf = 'pr'
homologacao = True

con = ComunicacaoSefaz(uf, certificado, senha, homologacao)
xml = con.status_servico('nfe')
print(xml.text)
```

  Mais exemplos no [Wiki](https://github.com/TadaSoftware/PyNFe/wiki)


Testes
-----------

```sh
python -m unittest
```


Documentação
-----------
- https://github.com/TadaSoftware/PyNFe/wiki
- http://pynfe.readthedocs.org/pt/latest/


Suporte
-----------
Se tiver qualquer problema or sugestão abra uma issue [aqui](https://github.com/TadaSoftware/PyNFe/issues) ou inicie uma discussão sobre um assunto [aqui](https://github.com/TadaSoftware/PyNFe/discussions).


Licença
-----------
PyNFe é licenciada sob a [LGPL-3.0](LICENSE).
