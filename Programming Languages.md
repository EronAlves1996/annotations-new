## C

- C's memory model is even simpler. It get compiled down to bare metal, and much information suffers erasure, same ways as Java generics. Scala native suggests that structs suffers erasure (it don't passes after compilation), because the access to CStructs are maded with positional-like fields (struct._1, struct._2).  