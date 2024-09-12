# useStorage()
use-localstorage-for-nextjs
## Hook para manipular o LocalStorage no NextJS

>> Finalidade:
- Para ser utilizado como um Hook em aplicações NextJS ou React que necessitam manipular o LocalStorage.


>> Funcionalidades
- Cria, Recupera e Remove itens através de uma função no Hook.

>> Utilização
- Foi desenvolvido usando NextJS na versão 14.2.x mas pode ser implementado em versões que suportam utilizar funções que rodam do lado do servidor (arquivos *.ts).

>> Implementação
- Pode ser utilizado dentro da pasta hooks (seguir a estrutura de pastas do projeto utilizado) com usando o nome useStorage.
- Para a implementação, basta importar em qualquer estrutura do lado do cliente para inicialização.

''Recomendo a utilização dentro de um Provider para que seja possível injetar o valor recuperado em qualquer função que utilize informações do LocalStorage.''

```
#typescript

interface Props {
  action: 'get' | 'remove' | 'set'
  key: string
  value?: string
}

export default function useStorage({ action, key, value }: Props) {
  const storage = () => {
    if (typeof localStorage !== 'undefined')
      switch (action) {
        case 'get':
          return localStorage.getItem(key)
        case 'remove':
          return localStorage.removeItem(key)
        case 'set':
          return localStorage.setItem(key, value!)
        default:
          return undefined
      }

    return
  }
  return storage()
}

```
