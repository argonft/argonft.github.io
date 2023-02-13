<!DOCTYPE html>
<html lang="tr">

<head>
  <meta charset="UTF-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ben İyiyim</title>
  <style>
    *,
    *::after,
    *::before {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: sans-serif;
    }

    html {
      font-size: 16px;
      line-height: 1.4;
      color: #747474;
    }

    /*** GENERICS ***/
    .bold {
      color: #595959;
      font-weight: bold;
    }

    /*** CARD ***/
    .card {
      width: 100%;
      border-radius: 5px;
      box-shadow: 0 0 10px 3px #e8e8e8;
    }

    #card__container {
      width: 100%;
      padding: 20px 15px;
    }

    #card__container .card:not(:last-child) {
      margin-bottom: 15px;
    }

    /*** STATUS BAR ***/
    .card>.card__status {
      color: white;
      font-weight: bold;
      padding: 3px 0;
      text-align: center;
      border-radius: 5px 5px 0 0;
      background-color: red;
    }

    .card>.card__status.success {
      background-color: #41a303;
    }

    .card>.card__status.warning {
      background-color: #ffc400;
    }

    .card>.card__status.danger {
      background-color: #ff0000;
    }

    /*** E: STATUS BAR ***/

    /*** HEADER ***/
    .card__header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 5px 10px;
      border-bottom: 1px solid #dddddd;
    }

    /*** E: HEADER ***/

    /*** DETAILS ***/
    .card__details {
      padding: 5px 10px;
    }

    .card__details>var {
      display: block;
      text-decoration: none;
      font-style: normal;
    }

    /*** E: DETAILS ***/
    /*** E: CARD ***/

    body {
      padding: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }

    h3 {
      text-align: center;
      margin-bottom: 20px;
    }

    .form-input label {
      text-align: left;
      width: 100%;
      display: block;
      font-size: 18px;
      padding-bottom: 4px;
    }

    .form-input+.form-input {
      margin-top: 20px;
      width: 100%;
    }

    form,
    .search-list {
      width: 90%;
      max-width: 500px;
      display: none;
    }

    .form-input input,
    .form-input select {
      padding: 10px;
      width: 100%;
      box-sizing: border-box;
    }

    .form-input {
      margin-bottom: 10px;
    }

    input,
    select {
      background: #ffffff;
      border-top: 1px solid rgba(0, 0, 0, 0.05);
      display: block;
      font-size: 1rem;
      line-height: 1.5;
      color: #495057;
      background-clip: padding-box;
      border: 1px solid #ced4da;
      border-radius: 0.25rem;
      outline-color: rgb(84 105 212 / 0.5);
      background-color: rgb(255, 255, 255);
      box-shadow: rgb(0 0 0 / 0%) 0px 0px 0px 0px,
        rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(0 0 0 / 0%) 0px 0px 0px 0px,
        rgb(60 66 87 / 16%) 0px 0px 0px 1px, rgb(0 0 0 / 0%) 0px 0px 0px 0px,
        rgb(0 0 0 / 0%) 0px 0px 0px 0px, rgb(0 0 0 / 0%) 0px 0px 0px 0px;
    }

    input[type="submit"],
    .selector button,
    .arama-butonu {
      background: #0a7b31;
      color: #fff;
      font-weight: bold;
      cursor: pointer;
      margin-top: 10px;
      padding: 15px;
      border: none;
      display: block;
      width: 100%;
    }

    input[type="submit"]:hover,
    .arama-butonu:hover {
      background: #25ac53;
    }

    form.open,
    .search-list.open {
      display: block;
    }

    .selector {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      width: 100%;
      max-width: 500px;
      padding: 30px;
      gap: 30px;
    }

    .selector.hidden {
      display: none;
    }

    .selector button {
      width: 100%;
      border: none;
      padding: 20px;
    }

    .selector button.depremzede {
      background-color: #8e1b07;
    }

    .selector button.depremzede-yakini {
      background-color: #c14d0a;
    }

    @media (max-width: 500px) {
      h3 {
        font-size: 16px;
        margin-top: 0;
      }
    }

    .search-list-unit {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
      gap: 10px;
    }

    .search-result {
      display: flex;
      flex-direction: column;
      padding: 10px;
      box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
      width: 200px;
    }

    .data {
      display: flex;
      flex-wrap: wrap;
    }

    label.info-element {
      display: none;
      color: red;
      margin-top: 10px;
      font-size: 16px;
    }

    label.info-element.showing {
      display: block;
    }
    .open form#searchForm {
      display: block;
      margin-left: auto;
      margin-right: auto;
    }
  </style>
</head>

<body>
  <!------ ANASAYFA ------>
  <h3>
    Beniyiyim.com, yalnızca depremzedeler ve yakınlarının haberleşmesini
    sağlamak için kullanılmaktadır.
  </h3>

  <div class="selector">
    <button class="depremzede" onclick="show('form')">DEPREMZEDEYİM</button>
    <button class="depremzede-yakini" onclick="show('.search-list')">
      DEPREMZEDE YAKINIYIM
    </button>
  </div>
  <!------ E: ANASAYFA ------>

  <!----- KAYIT SAYFASI ---->
  <form action="report" class="hidden" method="post">
    {% csrf_token %}

    <div class="form-input">
      <label for="input-isim">İsim</label><input id="input-isim" type="text" placeholder="İsim yazınız." name="isim"
        required>
    </div>
    <div class="form-input">
      <label for="input-sehir">Sehir</label>
      <select name="sehir" id="input-sehir" required>
        <option value disabled hidden selected>Şehir Seçiniz</option>
        <option value="Adana">Adana</option>
        <option value="Batman">Batman</option>
        <option value="Bitlis">Bitlis</option>
        <option value="Bingöl">Bingöl</option>
        <option value="Diyarbakır">Diyarbakır</option>
        <option value="Elazığ">Elazığ</option>
        <option value="Gaziantep">Gaziantep</option>
        <option value="Hakkari">Hakkari</option>
        <option value="Hatay">Hatay</option>
        <option value="Kahramanmaraş">Kahramanmaraş</option>
        <option value="Kilis">Kilis</option>
        <option value="Malatya">Malatya</option>
        <option value="Mardin">Mardin</option>
        <option value="Muş">Muş</option>
        <option value="Osmaniye">Osmaniye</option>
        <option value="Siirt">Siirt</option>
        <option value="Şırnak">Şırnak</option>
        <option value="Van">Van</option>
      </select>
    </div>
    <div class="form-input">
      <label for="input-adres">Adres</label><input id="input-adres" type="text" name="adres"
        placeholder="Adres ekleyiniz." required>
    </div>
    <div class="form-input">
      <label for="input-durum">Durum</label>
      <select name="durum" id="input-durum" required onChange="statusChanged(event)">
        <option value disabled hidden selected>Durum Seçiniz</option>
        <option value="iyiyim">İyiyim</option>
        <option value="yardim">
          Enkaz altında değilim fakat yardıma ihtiyacım var.
        </option>
        <option value="enkaz-altinda">Enkaz altındayım.</option>
      </select>
      <label class="info-element">Bu platform depremzedeler arası haberleşme amaçlıdır. Yardım taleplerinizi <a
          href="https://deprem.io">deprem.io</a>
        adresinden daha fazla insana iletebilirsiniz.</label>
    </div>
    <div class="form-input">
      <label for="input-tel">Telefon <small>(Opsiyonel)</small></label><input id="input-tel" type="tel" name="tel"
        placeholder="Telefon ekleyiniz (Örn: 05XXXXXXXXX)." />
    </div>
    <div class="form-input">
      <label for="input-not">Not <small>(Opsiyonel)</small></label><input id="input-not" type="text" name="not"
        placeholder="Not ekleyiniz.">
    </div>
    <div class="form-input"><input type="submit" value="Gönder" /></div>
  </form>
  <!----- E: KAYIT SAYFASI ---->

  <!----- ARAMA SAYFASI ---->
  <div class="search-list hidden">
    <form id="searchForm">
      <div class="form-input">
        <label>İsim Soyisim<small>(En az 3 karakter)</small></label>
        <input type="text" id="searchInputName" placeholder="İsim Soyisim arama" min="3" />
      </div>
      <div class="form-input">
        <label>Telefon Numarası<small>(En az 10 karakter)</small></label>
        <input type="tel" id="searchInputTel" placeholder="Örn: 05XXXXXXXXX" min="10" />
      </div>
      <div class="form-input">
        <button type="submit" class="arama-butonu" onclick="searchThis()">
          Ara
        </button>
      </div>
    </form>
  </div>
  <div id="card__container"></div>
  <!----- E: ARAMA SAYFASI ---->
  <script>
    
    var nameInput = document.getElementById("searchInputName");
    var telInput = document.getElementById("searchInputTel");
    var listElement = document.getElementById("card__container");

    function show(selector) {
      if (selector == "form") {
        document.querySelector("form").classList.toggle("open")
        document.querySelector(".search-list").classList.remove("open")
      }
      else {
        document.querySelector(".search-list").classList.toggle("open")
        document.querySelector("form").classList.remove("open")
      }

    }

    function formatDate(dateString) {
      const date = new Date(dateString);

      if (date.toString() === 'Invalid Date') {
        return '';
      }

      return new Intl.DateTimeFormat('tr-TR', { dateStyle: 'medium', timeStyle: 'short', timeZone: 'Turkey' })
        .format(date);
    };

    function mapStatus(status) {
      switch (status) {
        case "iyiyim":
          return "success";
        case "yardim":
        case "hastane-yatis":
          return "warning";
        case "enkaz-altinda":
        case "olu":
          return "danger";
        default:
          return "success";
      }
    }

    function generateCard({ isim, sehir, adres, durum, created_at, notlar }) {
      const elem = document.createElement("div");
      switch (durum) {
        case "iyiyim":
          var durumText = "İyiyim.";
          break;
        case "yardim":
          var durumText = "Enkaz altında değilim ancak yardıma ihtiyacım var.";
          break;
        case "hastane-yatis":
          var durumText = "Hastanede yatıyorum.";
          break;
        case "olu":
          var durumText = "Hayatını kaybetti."
          break;
        case "enkaz-altinda":
          var durumText = "Enkaz altındayım.";
          break;
        default:
          var durumText = "Bilinmiyor."          
      } 

      elem.className = "card";
      elem.innerHTML = `
          <div class="card__status bold ${mapStatus(durum)} field-durum"></div>
          <div class="card__header">
            <span class="bold field__isim"></span>
            <span class="bold field__sehir"></span>
          </div>
          <div class="card__details">
            <span class="bold">Adres:</span>
            <span class="field__adres"></span><br>
            <span class="bold">Not:</span>
            <span class="field__notlar"></span><br>
            <span class="date field__date"></span>
          </div>
        `;

      elem.querySelector(".field__isim").innerText = isim;
      elem.querySelector(".field__sehir").innerText = sehir;
      elem.querySelector(".field__adres").innerText = adres;
      elem.querySelector(".field-durum").innerText = durumText;
      elem.querySelector(".field__date").innerText = formatDate(created_at);
      elem.querySelector(".field__notlar").innerText = notlar;
      return elem;
    }



    //// preventdefault ile pure js XMLHttpRequest() kullanılarak post edilebilir.

    function searchThis() {
      var nameVal = "";
      var telVal = "";
      if (
        nameInput.value.length > 2
      ) {
        nameVal += "isim=" + nameInput.value;
      }
      if (telInput.value.length > 8) {
        telVal += "tel=" + telInput.value;
      }
      if (telInput.value.length > 9 || nameInput.value.length > 2) {
        let obj = fetch(
          "/search?" +
          nameVal +
          "&" +
          telVal,
          { mode: "no-cors" }
        )
          .then((response) => response.json())
          .then((data) => {
            listElement.innerHTML = ""
            if (data.length === 0) {
              alert("Sonuç bulunamadı.")
            } else if (data.error) {
              alert(data.error);
            } else {
              data.forEach(function (key, index) {
                var { isim, sehir, adres, durum, created_at, notlar } = key.fields;
                listElement.appendChild(
                  generateCard({ isim, sehir, adres, durum, created_at, notlar })
                );
              });
            };
          });
      } else {
        alert("İsim en az 3 karakter, telefon ise en az 9 karakter olmalıdır.");
      }
    }

    // durum "iyiyim" haricinde bir şey seçilirse bilgilendirme mesajı gösterir
    function statusChanged(event) {
      const selectedOption = event.target.value;
      const infoElement = document.querySelector(".info-element");

      if (selectedOption !== "iyiyim") {
        return infoElement.classList.add("showing");
      }

      infoElement.classList.remove("showing");
    }
    document.getElementById("searchForm").addEventListener('submit',function(e){ e.preventDefault(); });
  </script>
</body>

</html>