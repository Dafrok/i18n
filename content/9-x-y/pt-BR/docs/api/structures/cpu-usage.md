# Objeto UsoDaCPU

* Número `percentCPUUsage` - Porcentagem da CPU usada desde a última chamada de getCPUUsage. A primeira chamada retorna 0.
* `idleWakeupsPerSecond` Number - O número médio de ativações por segundo da CPU em estado ocioso desde a últama chamada para getCPUUsage. Primeira chamada retorna 0. Sempre retornará 0 no Windows.
