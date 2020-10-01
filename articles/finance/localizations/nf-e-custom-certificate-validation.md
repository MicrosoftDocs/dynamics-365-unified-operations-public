By turning on this feature, you enable a custom validation to allow a connection with the web services, required for transmitting of NF-e and getting authorization from SEFAZ.

The property “Server authentication purpose” from the certificate V5, issued by the Brazilian Root Certificate Authority, is disabled by default, requiring manual enablement. Nevertheless, under some circumstances, the automatic certificate update can disable this property, affecting the TLS connection, does not allowing it to be trusted, impacting the issuing of NF-e on production environments for states of Minas Gerais (MG) and Paraná (PR) states.

This update allows an alternative solution for validation of the certificate, permitting establishing a secure communication.

