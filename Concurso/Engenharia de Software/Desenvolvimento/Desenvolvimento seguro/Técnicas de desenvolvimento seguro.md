* def::**Desenvolvimento seguro**: zelo pela segurança da informação durante todo o ciclo de desenvolvimento de soluções de TI
* atributos essenciais de qualidade de um software { manutenibilidade, confiabilidade, eficiência, usabilidade }
* **Pontos importantes**: { segurança numa perspectiva institucional, cuidado ao longo de todo o ciclo de desenvolvimento }
* **Metodologias**:
	* [[SDL]]
	* [[CLASP]]
	* [[OWASP#^owasp-codificacao-segura|OWASP]]
	* def::**STRIDE**: acrônimo criado pela Microsoft para condensar perigos de segurança
		* **S**poofing (falsificação): falsificação de identidade de usuário
		* **T**ampering (adulteração): adulteração de integridade de informação/sistema
		* **R**epudiation: negação de execução de ato cometido por um usuário
		* **I**nformation Disclosure: divulgação indevida de informação
		* **D**enial of Service
		* **E**levention of Privilege: dar privilégios indevidamente
		* anki::Adicionar acrônimo STRIDE
* **Diretrizes para software seguro**:
	* ter senha forte/cofre de senhas
	* atualizar aplicações
	* documentação
	* validação de entradas
	* tratatamento de erros na aplicação + evitar deixar vazar mensagens de debug para usuário (pode fornecer informações úteis para explorar vulnerabilidades)
* **Conceitos**:
	* def::**Security by Design**: segurança da informação deve ser considerada já no desenvolvimento da arquitetura e design da solução ^def-security-by-design
	* def::**Security by Default**: a configuração padrão da solução deve ser a mais segura possível - a exemplo de remover toda biblioteca não necessária, desabilitar todo recurso não necessário ^def-security-by-default
	* def::**Security by Deployment**: devem ser disponibilizadas ferramentas e orientações que auxiliem os usuários/administradores finais a usar a solução com segurança - como ferramenta/documentação de atualização ^def-security-by-deployment