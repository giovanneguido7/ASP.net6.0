import React, { useState, useEffect } from 'react';

const Tabela = () => {
  const [dados, setDados] = useState([]);
  const [filtro, setFiltro] = useState('');

  useEffect(() => {
    // Faça a requisição à API e atualize os dados com o resultado
    // Aqui estou usando um mock para simplificar o exemplo
    const response = [
      { id: 1, nome: 'João', idade: 25 },
      { id: 2, nome: 'Maria', idade: 30 },
      { id: 3, nome: 'Pedro', idade: 35 },
      { id: 4, nome: 'Ana', idade: 28 },
    ];
    setDados(response);
  }, []);

  const handleInputChange = (e) => {
    setFiltro(e.target.value);
  };

  const dadosFiltrados = dados.filter((item) =>
    item.nome.toLowerCase().includes(filtro.toLowerCase())
  );

  return (
    <div>
      <input type="text" onChange={handleInputChange} value={filtro} />
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Idade</th>
          </tr>
        </thead>
        <tbody>
          {dadosFiltrados.map((item) => (
            <tr key={item.id}>
              <td>{item.id}</td>
              <td>{item.nome}</td>
              <td>{item.idade}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
};

export default Tabela;
