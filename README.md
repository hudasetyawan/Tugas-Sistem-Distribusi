# Tugas-Sistem-Distribusi
Cek saldo menggunakan nim dan postman

Buat file dengan nama file server_week7 :
------------------------------------

```python
from flask import Flask, request, jsonify

app = Flask(__name__)


@app.route('/api/request/cek-saldo', methods=['POST'])
def handle_request():
    try:
        # Get the JSON data from the request
        data = request.get_json()
        # saldo = data.get('saldo', 0)
        # nominal_transaksi = data.get('nominal_transaksi', 0)
        # saldo_akhir = saldo - nominal_transaksi
       
        # Process the data here (add your business logic)
        # For example:
        response_data = {
            'status': 'success',
            'message': 'Request processed successfully',
            'received_data': data,
            'news': 'halo budi data kamu sudah kami terima',
            # 'saldo': saldo,
            'nominal_transaksi': data.get('nominal_transaksi', 0),
            # 'saldo_akhir': saldo_akhir,
           
        }

        return jsonify(response_data), 200
   
    except Exception as e:
        error_response = {
            'status': 'error',
            'message': str(e)
        }
        return jsonify(error_response), 400

if __name__ == '__main__':
    app.run(debug=True, port=5000)

```
Cek dan uji menggunakan kodingan json berikut :

request berupa raw json
```json
{"nama":"budi", "nim":"1234567","saldo":"347000",
"nominal_transaksi":"15000"}
```
lalu gunakan url berikut :
```
url : http://127.0.0.1:5000/api/request/cek-saldo
```

Dan berikut hasil dari pengujian menggunakan postman :
<img width="1905" height="1011" alt="Screenshot 2025-11-05 145915" src="https://github.com/user-attachments/assets/74c6fedf-597d-4144-8f01-7289b29b4e52" />
