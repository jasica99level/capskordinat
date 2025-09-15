<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>Koordinat Botu</title>
<style>
  body { font-family: Arial, sans-serif; padding: 20px; background: #f0f0f0; }
  h1 { color: #333; }
  .dunya { margin: 5px 0; }
  #sonuc { margin-top: 20px; font-weight: bold; }
</style>
</head>
<body>

<h1>Dünya ve Koordinat Botu</h1>

<p>Hangi dünyadayız? Koordinat gir:</p>
<label>X: <input type="number" id="x"></label>
<label>Y: <input type="number" id="y"></label>
<label>Z: <input type="number" id="z"></label>
<button onclick="hesapla()">En Yakın Dünyayı Bul</button>

<div id="sonuc"></div>

<script>
// Örnek dünya koordinatları (rastgele değerler)
const dunyalar = {
    sancak: {x: 100, y: 64, z: 200},
    yakamoz: {x: -50, y: 64, z: 300},
    avrasya: {x: 200, y: 64, z: -100},
    pruva: {x: 0, y: 64, z: 0},
    velena: {x: 150, y: 64, z: 150},
    flador: {x: -100, y: 64, z: -200},
    astra: {x: 50, y: 64, z: -50}
};

function hesapla() {
    const x = parseInt(document.getElementById('x').value);
    const y = parseInt(document.getElementById('y').value);
    const z = parseInt(document.getElementById('z').value);

    let enYakın = null;
    let minMesafe = Infinity;

    for (const [dunya, coord] of Object.entries(dunyalar)) {
        const mesafe = Math.sqrt(
            (coord.x - x) ** 2 +
            (coord.y - y) ** 2 +
            (coord.z - z) ** 2
        );
        if (mesafe < minMesafe) {
            minMesafe = mesafe;
            enYakın = dunya;
        }
    }

    document.getElementById('sonuc').innerHTML = `
        En yakın dünya: <b>${enYakın}</b><br>
        Mesafe: <b>${Math.round(minMesafe)}</b>
    `;
}
</script>

</body>
</html>
