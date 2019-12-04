---
author: Isaac Eldridge <isaac.eldridge@puppet.com\>
---

# SSL and certificates

Network communications and security in Puppet Enterprise are based on HTTPS, which secures traffic using X.509 certificates. PE includes its own CA tools, which you can use to regenerate certs as needed.

-   **[Regenerating certificates: monolithic installs](regenerating_certificates_monolithic_installs.md#)**  
In some cases, you may find that you need to regenerate the certificates and security credentials \(private and public keys\) generated by PE's built-in certificate authority \(CA\). For example, you may have a Puppet master that you need to move to a different network in your infrastructure, or you may find that you need to regenerate all the certificates and security credentials in your infrastructure due to an unforeseen security vulnerability.
-   **[Regenerating certificates: split installs](regenerating_certificates_split_installs.md#)**  
In some cases, you may find that you need to regenerate the SSL certificates and security credentials \(private and public keys\) that are generated by PE's built-in certificate authority \(CA\). For example, you may have a Puppet master you need to move to a different network in your infrastructure, or you may find you need to regenerate all the certificates and security credentials in your infrastructure due to an unforeseen security vulnerability.
-   **[Individual PE component cert regeneration \(split installs only\)](individual_pe_component_cert_regeneration.md#)**  
If you encounter a security vulnerability, or need to change your certificates for some other reason \(for example, if you have a hostname change\), you can regenerate the certificate and security credentials \(private and public keys\) generated for the PE components.
-   **[Regenerate Puppet agent certificates](regenerate_puppet_agent_certificates.md)**  
From time to time, you might encounter a situation in which you need to regenerate a certificate for an agent. Perhaps there is a security vulnerability in your infrastructure that you can remediate with a certificate regeneration, or maybe you're receiving SSL errors on your agent that are preventing you from performing normal operations.
-   **[Regenerate compile master certs](regenerate_compile_master_certificates.md)**  
From time to time, you may encounter a situation in which you need to regenerate a certificate for a compile master. Perhaps there is a security vulnerability in your infrastructure that you can remediate with a certificate regeneration, or maybe you're receiving strange SSL errors on your compile master that are preventing you from performing normal operations.
-   **[Using an External Certificate Authority with Puppet Enterprise](using_an_external_certificate_authority_with_pe.md#)**  
The different parts of Puppet Enterprise \(PE\) use SSL certificates to communicate securely with each other, and PE uses its own certificate authority \(CA\) to generate and verify these credentials. However, you may already have your own CA in place and wish to use it instead of PE's integrated CA.
-   **[Use a custom SSL certificate for the console](use_a_custom_ssl_cert_for_the_console.md)**  
The console uses a certificate signed by PE's built-in certificate authority \(CA\). Since this CA is specific to PE, web browsers don't know it or trust it, and you have to add a security exception in order to access the console. You may find that this is not an acceptable scenario and want to use a custom CA to create the console's certificate.
-   **[Generate a custom Diffie-Hellman parameter file](generate_custom_dh_parameter_file.md)**  
The "Logjam Attack" \(CVE-2015-4000\) exposed several weaknesses in the Diffie-Hellman \(DH\) key exchange. To help mitigate the "Logjam Attack," PE ships with a pre-generated 2048 bit Diffie-Hellman param file. In the case that you don't want to use the default DH param file, you can generate your own.
-   **[Disable TLSv1 in PE](disable_tlsv1_in_PE.md)**  
You can disable TLSv1 in PE to comply with standards as necessary.
