# ASP.net6.0

import React from 'react';

function VerificarString(props) {
  const { texto } = props;

  // Verifica se a string tem 10 números
  const verificarString = (str) => {
    const regex = /\d/g; // Expressão regular para verificar números
    const numeros = str.match(regex); // Filtra os números da string

    if (numeros && numeros.length === 10) {
      return str; // Se já tiver 10 números, retorna a string sem alterações
    } else if (numeros && numeros.length < 10) {
      // Se tiver menos de 10 números, acrescenta um 0 no início
      const zerosFaltantes = 10 - numeros.length;
      const zeros = Array(zerosFaltantes).fill(0).join(''); // Cria uma string com os zeros
      return `${zeros}${str}`;
    }
  };

  return (
    <div>
      <p>Texto original: {texto}</p>
      <p>Texto modificado: {verificarString(texto)}</p>
    </div>
  );
}

export default VerificarString;




import React from 'react';
import VerificarString from './VerificarString';

function App() {
  return (
    <div>
      <VerificarString texto="1234567890" />
    </div>
  );
}

export default App;
