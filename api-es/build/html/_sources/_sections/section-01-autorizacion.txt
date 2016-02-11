1. Autorización
===============

1. Lo primero que se hace es tratar de identificar la cuenta (Account) mediante el dominio. Si no se puede identificar no se permite el acceso.

2. Luego se intenta identificar la auth_key (privada o pública). Si no se puede indentificar no se permite el acceso.

3. Si la auth_key es publica se chequea el referer. Si no se puede identificar no se permite el acceso.

4. Se trata de identificar al usuario. Si no se puede identificar se trata de un usuario 'anónimo


