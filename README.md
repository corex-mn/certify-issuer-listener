# Certify issuer listener
Хөгжүүлэлт хийсэн node -ийн хувилбар: `v14^`
## Суулгах заавар
npm install

## Асаах заавар
Кодийг ажиллуулахдаа дэлгэрэнгүй логтой ажиллуулах бол `node ./index.js --verbose`, бусад үед зүгээр `node ./index.js` -аар ажиллуулна.

## Анхаарах зүйлс:
1. Код ажиллахдаа .env файлаас ажиллах орчны утгаа авч байгаа тул доторх утгуудыг сольж асаана уу.
2. Код ажиллахдаа go-corex -ийн үүсгэсэн *.ipc файлаас уншдаг учраас go-corex node заавал ажиллаж байх ёстой.
3. block_numbers гэсэн файлд хамгийн сүүлд уншсан блокын дугаарыг хадгалж, дахин кодыг ажиллуулахдаа хадгалсан файлаас блокын дугаараас эхлэж ухаалаг гэрээний эвентийг сонсож ажиллаж байгаа.
```javascript
contract.events.Issued({
        // computedBlock нь хамгийн сүүлийн уншсан блок,
        // үүнийг дахин уншихгүй тулд нэгийг нэмэж алгасна.
        fromBlock: computedBlock + 1,
}
```

## Kafka -руу явуулж буй өгөгдлийн бүтэц:
Өгөгдлийг явуулахдаа value гэсэн объектод JSON.stringify хийж явуулж байгаа.

```json
  message: {
    blockNumber: integer,
    issuer: string,
    hash: string,
    metaHash: string,
    certNum: string,
    timestamp: string
  }
```

