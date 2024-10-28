# EJERCICIO 4
Ejercicio 4: Implementa un trait Loggable que registra mensajes con fecha y hora, y una clase Producto que usa este trait para registrar cada cambio de precio.

<?php

require_once 'producto.php'; 

$producto = new Producto("Zapatos", 50);

ç
$producto->setPrecio(60); 
$producto->setPrecio(55); 
?>

<?php

require_once 'loggable.php'; // Incluir el trait Loggable

class Producto {
    private $nombre;
    private $precio;

    public function __construct($nombre, $precio) {
        $this->nombre = $nombre;
        $this->precio = $precio;
    }
    public function setPrecio($nuevoPrecio) {
       
        $this->log("Cambio de precio: de {$this->precio} a {$nuevoPrecio}");
        $this->precio = $nuevoPrecio; 
    }

    public function getPrecio() {
        return $this->precio; 
    }
    public function getNombre() {
        return $this->nombre; 
    }
    use Loggable; 
}
?>

<?php

trait Loggable {
    public function log($mensaje) {
        echo $mensaje . "\n";
    }
}
?>
