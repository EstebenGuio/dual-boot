# Dual boot instalación   windows 10 & ArcoLinux

## Windows

* A. Crear imagen ISO:
    * Descarga la herramienta: [Create Windows 10 installation media aquí](https://go.microsoft.com/fwlink/?LinkId=691209)
    * Seguir el wizard y crear una USB booteable con la imagen: 
    * > __Nota:__ La USB debe tener como mínimo 8GB de espacio
    * Una vez creado, inciar el pc para la instalación del sistema operativo
    * > __Nota:__ Prestar atención a si se usa UEFI o BIOS
    * > __Nota:__ Se asume que la persona que está siguiendo este proceso sabe particionar discos, sino, usar san google.
    * Creación particion EFI:
        >__NOTA:__ Para evitar problemas que pueden saltar con las diferentes distros de linux, es mejor crear la partición EFI del disco de forma manual, así podemos controlar el sizing que queremos darle. Si se hace de forma automática el sistema creará una de 100MB
        * Al llegar a la venta de partición de discos usar el comando: `Shift`+`F10` <kbd>Enter</kbd>
        * Ejecutar `diskpart` <kbd>Enter</kbd>
        * Ejecutar `list disk` <kbd>Enter</kbd>
        * Ejecutar `select disk 0` <kbd>Enter</kbd> Reemplazar el 0 por el disco donde se desea crear la partición
        * Ejecutar `create partition efi size=500` <kbd>Enter</kbd>
        * Ejecutar `exit` <kbd>Enter</kbd> dos veces
    * Crear partición de windows (No crear la partición de linux, esa se deja como espacio sin usar)
    * Y como todo en windows, next, next, next.....

## Linux

* B. En mi caso voy a usar arco linux, si es el caso, descarga la imagen de (https://www.arcolinux.info/downloads/)[https://www.arcolinux.info/downloads/]

    * Descargar rufus de (https://rufus.ie/en/)[https://rufus.ie/en/]
    * Seleccionar la memoria USB, la ISO y crear disco, todo por defecto
    * Poner la USB en el pc a instalar y reiniciar
    * Presionar la tecla  <kbd>f8</kbd> o <kbd>f12</kbd>, la que corresponda para el menú de boot
    * Seleccionar la memoria USB y luego la opción de instalación
    * Y aquí puede pasar una de dos cosas:
        * Si te abre el instalador y tiene interfaz gráfica como arcolinux, Fe li ci da des, igual que en windows, next, next.
        Sino, pueden salir multiples errores, aquí vamos a ver el error: `You need to load the kernel first`, entonces para cargar el kernel:
        * > __NOTA__ Este error se soluciona muchas veces simplemente desactivando el BOOT Seguro en las opciones de BIOS/UEFI
        * En el menú de opciones de instalación, usar la tecla <kbd>esc</kbd> para entrar al grub
        * Identificar dónde está el kernel de linux, debería estar dentro de la memoria que tiene el sistema a instalar, entonces usar `ls`
        * Generalmente está en `(hd0, msdos1)/boot/` o `(hd0, gpt1)/boot`
        * En el caso de las ISO de arch es: `(hd0, [La que haya mostrado datos])/arch/boot/x86_64/vmlinuz-linux`
        * Una vez encontrado se ejecuta: `insmod linux`
        * Luego `linux (hd0, [La que haya mostrado datos])/arch/boot/x86_64/vmlinuz-linux`|
        * Finalmente `boot`

    * Luego ya debería abrir normalmente el instalador de arcolinux con Calamares.

    Thx por leer.
        
        


