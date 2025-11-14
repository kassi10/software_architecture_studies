- cqrs
- aws well architecture
- Multi tenant
- 12 factor app
- lock distribuido
- invalidacao da cache
- SAD (DOCUMENTACAO)



Assinale os pontos que devemos levar em consideração na hora de escalar um sistema, independente se ele for monolito ou microsserviço?
R:Disco efêmero, logs devem ser armazenados externamente, sessões do usuário devem ser armazenadas externamente, não deve armazenar estado.
Explicação:
Ao escalar qualquer sistema (monólito ou microsserviços), é fundamental:

Disco efêmero: instâncias podem morrer ou serem recriadas, então nada deve depender do disco local.

Logs externos: usar ferramentas como ELK, Loki, CloudWatch, etc.

Sessões externas: usar Redis ou outro storage compartilhado.

Stateless: cada instância deve ser facilmente replicável e descartável.