# Objeto IpcMainEvent herda de `Event`

* `processId` Integer - The internal ID of the renderer process that sent this message
* `frameId` Integer - O ID do quadro do renderizador que enviou esta mensagem
* `returnValue` any - Set this to the value to be returned in a synchronous message
* `sender` WebContents - Retorna o `webContents` que enviou a mensagem
* `ports` MessagePortMain[] - Uma lista de MessagePorts que foram transferidos com esta mensagem
* `reply` Função - Uma função que enviará uma mensagem IPC para o quadro renderizador que enviou a mensagem original que você está usando atualmente.  You should use this method to "reply" to the sent message in order to guarantee the reply will go to the correct process and frame.
  * `channel` String
  * `...args` any[]
