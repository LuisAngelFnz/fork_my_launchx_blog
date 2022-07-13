---
title: "BUG Terminator se presiona teclas 2 veces en modo grupo de pestañas"
date: 2022-07-13
description: 'Solución a problema con Terminator de grupo de pestañas'
---

Recientemente me encontre con este bug en Terminator<br>.
cuando agrupo pestañas y empiezo a escribir se duplica lo tecleado ejemplo:

[example](../static/images/post_3/before.png)

# Versiones de mi terminator y fedora
- terminator 2.1.1
- Fedora 33
- Python 3.10.5

# Solución(como super usuario):

- Abrir el siguiente archivo con tu editor favorito
| vim /usr/lib/python3.10/site-packages/terminatorlib/layoutlauncher.py

- antes de la linea que contiene *if __name__ == '__main__':*

- Agregar el siguiente código:


| try:
|    del os.environ['GTK_IM_MODULE']
| except Exception as e:
|     print(e)


[example](../static/images/post_3/code.png)


- Guardamos he iniciamos terminator con normalidad

[example](../static/images/post_3/after.png)

- Y listo espero les sirva


