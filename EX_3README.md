# EJERCICIO 3
Ejercicio 3: Crea una clase SensorController que asigna valores aleatorios a cinco sensores y permite evaluar fórmulas matemáticas sobre estos valores, simulando el control de dispositivos.

<?php
require_once 'SensorController.php';

$controller = new SensorController();


for ($i = 0; $i < 5; $i++) {
    $controller->generarValorAleatorio($i);
    echo "Sensor " . $i . ": " . $controller->obtenerValorSensor($i) . "<br>";

    $formula1 = "sensor * 2 / 24";
    $formula2 = "sensor / 2";
    $formula3 = "sensor + 2";

    echo "Resultado de '" . $formula1 . "': " . $controller->evaluarFormula($i, $formula1) . "<br>";
    echo "Resultado de '" . $formula2 . "': " . $controller->evaluarFormula($i, $formula2) . "<br>";
    echo "Resultado de '" . $formula3 . "': " . $controller->evaluarFormula($i, $formula3) . "<br><br>";
}
?>
<?php
class SensorController {
    private $sensores = [];

    
    public function generarValorAleatorio($indice) {
        $this->sensores[$indice] = rand(0, 4095);
    }

    
    public function obtenerValorSensor($indice) {
        return $this->sensores[$indice] ?? null;
    }

    
    public function evaluarFormula($indice, $formula) {
        $sensor = $this->obtenerValorSensor($indice);
        if ($sensor === null) {
            return "Sensor no inicializado.";
        }

        
        return eval("return " . str_replace("sensor", $sensor, $formula) . ";");
    }
}
?>
