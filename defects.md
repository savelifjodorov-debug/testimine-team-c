Defektiraportid – inventory API
D-01 · GET /items/:id tagastab tundmatu id korral 200 null
Nõue: REQ-API-02
Leidis: TC-03
Raskusaste: High
Koht koodis: server.js, marsruut GET /items/:id
Sammud: curl -s -i localhost:3000/items/999
Oodatud: 404, keha { "error": "not found" }
Tegelik: 200, keha null
Oleks: open

D-02 · POST /items võtab vastu negatiivse koguse (-1)
Nõue: REQ-API-03
Leidis: TC-06
Raskusaste: High
Koht koodis: server.js, funktsioon validate
Sammud: curl -s -i -X POST localhost:3000/items -H 'Content-Type: application/json' -d '{"sku":"C-3","qty":-1}'
Oodatud: 400, keha { "error": "invalid qty" }
Tegelik: 201, kirje loodud kogusega -1
Oleks: open

D-03 · DELETE /items/:id tagastab 204 asemel 200 koos kehaga
Nõue: REQ-API-06
Leidis: TC-09
Raskusaste: Medium
Koht koodis: server.js, marsruut DELETE /items/:id
Sammud: curl -s -i -X DELETE localhost:3000/items/1
Oodatud: 204 No Content, keha puudub
Tegelik: 200 OK, keha { "deleted": true }
Oleks: open
