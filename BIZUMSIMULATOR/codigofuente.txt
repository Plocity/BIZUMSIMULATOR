from collections import namedtuple

Cartera = namedtuple('Cartera', 'numero, cantidad')


def enviar_bizum(cartera: Cartera, usuario: str) -> Cartera:
    print('Dinero a enviar a', usuario, ':')
    try:
        dinero = int(input())
    except ValueError:
        print('Por puto payaso te quedaste sin dinero :)')
        chistoso2 = cartera.cantidad - cartera.cantidad
        print('Perro Sanchez ha recibido tu Bizum de', cartera.cantidad, '€')
        return Cartera(cartera.numero, chistoso2)

    print('Estas seguro que quieres enviar', dinero, '€ a', usuario, '?')
    print('Responder S o N')
    respuesta = input()
    if respuesta == 'S' or respuesta == 's':
        nueva_cantidad = cartera.cantidad - dinero
        print(usuario, 'ha recibido tu bizum de', dinero, '€')
        return Cartera(cartera.numero, nueva_cantidad)
    elif respuesta == 'N' or respuesta == 'n':
        return cartera
    else:
        print('Por puto payaso te quedaste sin dinero :)')
        chistoso = cartera.cantidad - cartera.cantidad
        print('Perro Sanchez ha recibido tu Bizum de', cartera.cantidad, '€')
        return Cartera(cartera.numero, chistoso)
    

def main():
    print('Introduzca su saldo:')
    try:
        saldo = int(input('Saldo:'))
    except ValueError:
        print('Payaso de mierda, ahora te quedaste sin dinero')
        saldo = 0

    print('Introduzca destinatario')
    destinatario = input()
    
    billetera = Cartera(1111_2222_3333_4444, saldo)
    nueva_billetera = enviar_bizum(billetera, destinatario)
    print('Datos de su cuenta de banco:', nueva_billetera)

if __name__ == '__main__':
    main()
    import sys
    if sys.platform.startswith('win'):
        import msvcrt
        print("Presiona cualquier tecla para cerrar la sesion...")
        msvcrt.getch() # Espera a que se presione una tecla
        sys.exit()
