`瀏覽器`在使用者瀏覽網站時，幫其檢查網站的安全性。

>輸入資料在傳輸時，是否有加密。

---
## SSL基礎 
---

### 種類

* 驗證方式 區分 : 一般、進階、商用。
* 支援程度 區分 : 單一位址、萬用位址、多重位址。

>驗證方式 : 驗證 `DNS 擁有權`。

---
## 申請流程、所需資訊
---

* ### 私有金鑰 – Pirvate Key
* ### 簽署要求 – Certificate Signing Request(CSR)
* ### 憑證 – CRT
* ### 中繼憑證 – PEM or CRT

## 流程 : 

* 申請 : 
>產生私有金鑰 -> 產生簽署要求 -> 將簽署要求傳給廠商 -> 付款 -> 等待驗證

* 安裝 : 
>取得憑證 -> 下載中繼憑證 -> 上傳到伺服器 -> 設定網頁伺服器(Apache) -> 完成

---
## `產生私有金鑰`
---
Win環境 : 可下載 OpenSSL。


    -----BEGIN RSA PRIVATE KEY-----
    (亂碼)
    -----END RSA PRIVATE KEY-----

>這個檔案就是你的私有金鑰，建議標示清楚並妥善保存。

---
## `產生憑證簽署要求（CSR）`
---
因為 `Pirvate Key` 不可交到任何人手上。

>所以給 `憑證中心` 的簽署，要透過 CSR 來完成。

憑證中心收到 CSR，解開後，就可以驗證身分。

驗證OK後，會把 Pirvate Key 進行簽署，最後再把簽署後資料回傳，即 `最終憑證`。

---
## 產生 CSR 填寫資訊
---
>建議在產生 CSR 的時候用你的域名來當檔名。

* Country Name (2 letter code) [AU]

  二字元國家代碼。ex : `TW`

* State or Province Name (full name) [Some-State]

  州或省。ex : `Taiwan`

* Locality Name (eg, city) []

  城市。ex : `Taipei`

* Organization Name (eg, company) [Internet Widgits Pty Ltd]

  組織或公司名稱。ex : （填寫`公司英文名稱`）

* Organizational Unit Name (eg, section)

  申請的部門名稱。ex : 如果是EV，可能會電訪。

* Common Name (e.g. server FQDN or YOUR name) []

  簽署名稱，即 `網址`。

* Email Address []
  
  電子信箱。

* A challenge password []

  密碼。若不設定，直接 enter，設定之後一定要記住。

* An optional company name []

  其他的公司名稱。若不設定，直接 enter。

### 完成之後 : 
會得到 `OOO.key` 與 `OOO.csr`。

>建議OOO用域名。

此 OOO.csr 即是給憑證中心的 CSR 檔。