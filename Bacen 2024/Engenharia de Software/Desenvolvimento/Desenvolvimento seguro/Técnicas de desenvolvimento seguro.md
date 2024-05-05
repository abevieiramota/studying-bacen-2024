---
relacionado: "[[Segurança da Informação/Básico|Básico]]"
material: https://provasdeti.nutror.com/curso/93ee181f34dea561421ed10f15614d24d58ce143
---
* def::**Desenvolvimento seguro**: deve-se zelar pela segurança durante todo o ciclo de desenvolvimento de soluções de TI
* atributos essenciais de qualidade de um software { manutenibilidade, confiabilidade, eficiência, usabilidade }
* objetivos principais de explorações de vulnerabilidades { causar indisponibilidade, acesso indevido a dados, causar prejuízo à integridade dos dados }
* pontos importantes
	* segurança deve ser tratada numa perspectiva institucional
	* passa por todos os ciclos e momentos de tratamento da informação
		* o desenvolvimento é uma etapa crítica 
* **Metodologias**
	* [[SDL]]
	* [[CLASP]]
	* [[OWASP#^owasp-codificacao-segura|OWASP]]
	* **STRIDE** -> acrônimo criado pela Microsoft para condensar perigos de segurança
		* **S**poofing (falsificação) -> falsificação de identidade de usuário
		* **T**ampering (adulteração)-> adulteração de integridade de informação/sistema
		* **R**epudiation -> negação de execução de ato cometido por um usuário
		* **I**nformation Disclosure -> divulgação indevida de informação
		* **D**enial of Service
		* **E**levention of Privilege -> dar privilégios indevidamente
* Diretrizes para software seguro
	* ter senha forte/cofre de senhas
	* atualizar aplicações
	* fuzzing -> envia entradas randômicas (com características que tendem a gerar falhas, como uso de caracteres não visuais), para identificar falhas
	* documentação
	* validação de entradas
	* tratatamento de erros na aplicação + evitar deixar vazar mensagens de debug para usuário (pode fornecer informações úteis para explorar vulnerabilidades)
* **Conceitos**
	* def::**Security by Design**: segurança da informação deve ser considerada já no desenvolvimento da arquitetura e design da solução ^def-security-by-design
	* def::**Security by Default**: a configuração padrão da solução deve ser a mais segura possível - a exemplo de remover toda biblioteca não necessária, desabilitar todo recurso não necessário ^def-security-by-default
	* def::**Security by Deployment**: devem ser disponibilizadas ferramentas e orientações que auxiliem os usuários/administradores finais a usar a solução com segurança - como ferramenta/documentação de atualização ^def-security-by-deployment