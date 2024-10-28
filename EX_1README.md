# EJERCICIO 2
Ejercicio 2: Define una clase Empleado con un constructor para establecer nombre y sueldo, e incluye un método que verifica si el empleado debe pagar impuestos cuando su sueldo supera los 2000€.

<?php
require_once 'Empleado.php';


$empleado1 = new Empleado("JULIAN", 2500);
$empleado2 = new Empleado("LAMINE", 1800);

$empleado1->verificarImpuestos();
$empleado2->verificarImpuestos();
?>

<?php
class Empleado {
    public $nombre;
    public $sueldo;

    // Constructor
    public function __construct($nombre, $sueldo) {
        $this->nombre = $nombre;
        $this->sueldo = $sueldo;
    }

    
    public function verificarImpuestos() {
        if ($this->sueldo > 2000) {
            echo $this->nombre . " debe pagar impuestos.<br>";
        } else {
            echo $this->nombre . " no debe pagar impuestos.<br>";
        }
    }
}
?>
