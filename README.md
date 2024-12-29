Aqui está uma implementação equivalente em TypeScript para a função antiInjection. TypeScript não possui algumas funções nativas do PHP como addslashes diretamente, mas podemos usar abordagens similares com métodos JavaScript:

typescript
Copiar código
function antiInjection(str: string): string {
    // Remove possíveis espaços extras no início e no final
    str = str.trim();

    // Remove tags HTML e scripts
    str = str.replace(/<\/?[^>]+(>|$)/g, "");

    // Escapa caracteres especiais (equivalente ao addslashes no PHP)
    str = str.replace(/['"\\]/g, '\\$&');

    return str;
}

// Exemplo de uso
const userInput = `<script>alert('injection')</script> SELECT * FROM users WHERE id='1'`;
const sanitizedInput = antiInjection(userInput);
console.log(sanitizedInput);
Explicação do código:
trim: Remove os espaços no início e no final da string, equivalente ao trim do PHP.
Remoção de tags HTML e PHP: Usa uma expressão regular para remover qualquer tag HTML ou script na string (/<\/?[^>]+(>|$)/g).
Escapar caracteres especiais: Implementa um comportamento similar ao addslashes, escapando aspas simples, aspas duplas e barras invertidas.
Observação:
Embora esta função seja útil para lidar com entradas de usuários, ela não substitui um ORM ou medidas de segurança como prepared statements ao lidar com banco de dados.
