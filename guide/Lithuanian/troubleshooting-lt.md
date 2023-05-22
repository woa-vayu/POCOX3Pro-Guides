## Problemų šalinimas


### Įrenginys gali pasileisti į Android sistemą, bet ne į sistemos paleidyklę (bootloader)

Reikiami įrankiai:

- [platform-tools](https://developer.android.com/studio/releases/platform-tools)

Šią problemą sukelia particijos su pavadinimais, kurių sistemos paleidyklė (bootloader) negali apdoroti, norint tai sutvarkyti:

- Paleiskite telefoną į recovery režimą

- Prijunkite telefoną prie kompiuterio

- Atidarykite komandinę eilutę kompiuteryje

- Paleiskite komandą ```adb shell```

- Paleiskite komandą ```parted```

- Paleiskite komandą ```print``` kad išvardyti visas particijas

- Ieškokite particijų, kurios turi tarpus pavadinimuose, pvz "Basic Data Partition" ir įsiminkite jų particijų numerius

- Dabar paleiskite komandą ```rm <vol number>``` pvz ```rm 36```



### Liečiamo ekrano palietimai netikslūs/aukštyn kojomis

Jūs neteisingai sukonfigūravote liečiamojo ekrano draiverius, norint tai sutvarkyti:

- [Sekite šią gido dalį](https://github.com/woa-vayu/Port-Windows-11-Poco-X3-pro/blob/main/guide/Lithuanian/2-install-lt.md#patikrinkite-kokią-ekrano-panelę-turi-jūsų-telefonas)
