# pds

Trabalho Prático sobre Testes de Software

Repositório 1: https://github.com/tannerlinsley/react-query
![image](https://user-images.githubusercontent.com/50335892/148748566-82e1e9ad-a8bb-46f1-9acc-14c4f709da28.png)
.

O teste escolhido no repositório do react-query se refere a capacidade do hook em renderizar o último estado de data mesmo que o react descarte algumas renderizações, como em *memoizações*. Ao realizar um *setNewState* com o valor idêntico ao anterior, o React opta por descartar um *re-render*, pois nada mudou. Entretanto, o *setQueryData* teve uma mudança no valor que deve ser atualizada, mesmo que o hook tenha indicado que não. Ao final do teste, o Jest verifica se mesmo com essa mecânica do React o valor final da *queryKey* foi devidamente atualizado para *new*. Esse cenário é extremamente comum e é importante que a biblioteca mantenha um *tracking* da situação para evitar um comportamento extremamente perigoso sendo distribuído em massa para milhares de aplicações que usam o React Query.


Repositório 2: https://github.com/react-hook-form/react-hook-form
![image](https://user-images.githubusercontent.com/50335892/148750011-5745832f-4be7-484f-8575-a5ba31213605.png)
.

O teste escolhido faz parte do grupo de testes relacionados ao _onChange_. O componente utilizado na renderização é por _default_, _required_. É disparado um evento de mudança de valor que adiciona um espaço e logo após é adicionado um outro evento de mudança de valor do campo do componente que retira esse espaço. Ao final do evento o useForm deve perceber que um campo _required_ previamente preenchido está com valor _null_. Nesse caso então o aviso de campo obrigatório deve ser renderizado e é exatamente isso que o teste pede na sua consulta _expect_. É outro teste básico, mas muito importante para entender se o useForm está preservando sua compatibilidade de validação de formulário com o HTML5, afinal toda a lógica é construída através do _state_ do React e do _Virtual DOM_.


Repositório 3: https://github.com/react-bootstrap/react-bootstrap
![image](https://user-images.githubusercontent.com/50335892/148750872-ad5cf74c-f65f-4b1d-b767-0bfd77ed8ecb.png)
.

Por ser uma biblioteca visual, o react-bootstrap conta com testes unitários mais focados na parte de renderização e entendimento se os visuais estão de acordo com o necessário. O teste acima cobra que o componente tenha a prop className extendida corretamente das props nativas do React. A prova de sucesso é tirada quando se consulta o classList do elemento _Card_. Testes que tem relação com compatibilidade de props nativas ou de outros frameworks são muito valiosos em updates de dependências, auxiliando no entendimento de quando há _breaking changes_ que precisam ser solucionadas antes de uma atualização.
