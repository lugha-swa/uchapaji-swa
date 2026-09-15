# uchapaji-swa

Msomaji wa fonti za TrueType (.ttf) na kijazaji cha glyph (rasterizer),
kwa Swa safi -- hakuna FreeType, hakuna maktaba yoyote ya nje ya
uchapaji. Hii ni kipande kinachokosekana kati ya "kuweza kuchora
maumbo" (kazi ya DRM/KMS iliyopo tayari kwenye
[Dominion](https://github.com/Kandemark/dominion)) na "kuweza kuchora
herufi halisi".

## Wigo wa toleo hili

Imethibitishwa dhidi ya fonti HALISI
(`/usr/share/fonts/liberation/LiberationSans-Regular.ttf`), si data
ya kubuni:

- Mwelekeo wa jedwali (table directory), `head`, `maxp`, `loca`,
  `glyf` -- baiti-kwa-baiti, dhidi ya thamani zilizothibitishwa kwa
  mkono (Python, uchunguzi wa moja kwa moja wa faili halisi) kabla ya
  kuandika msimbo wowote wa Swa.
- `cmap` muundo 4 pekee (BMP/Kilatini -- inatosha kabisa kwa
  Kiswahili, ambacho ni lugha ya alfabeti ya Kilatini).
- Glyph "rahisi" (simple glyph) pekee -- SI glyph za "kiwanja"
  (composite), ambazo hurejelea glyph nyingine na huongeza utata wa
  kweli, nje ya wigo wa toleo hili.
- Curves za quadratic Bezier, ikiwemo kanuni HALISI ya TrueType ya
  "pointi ya katikati iliyodokezwa" kati ya pointi mbili za
  off-curve mfululizo.
- Kijazaji cha scanline kwa kanuni ya NONZERO WINDING (kanuni rasmi
  ya TrueType) -- kimethibitishwa kikamilifu na glyph zenye shimo la
  ndani (O: shimo 1, B: mashimo 2).

**Halijashughulikiwa kwa makusudi** (kazi ijayo): glyph za kiwanja,
anti-aliasing (mpaka wa sasa ni mweusi/mweupe tu, hakuna kivuli cha
mpito), hinting, kerning, na kuunganisha na mfumo wa onyesho wa
DRM/KMS wa Dominion (kipande hiki kinatoa bafa ya pikseli tu, si
uoneshaji wa moja kwa moja).

## Muundo

```
msingi/ttf.swa      -- msomaji wa faili za .ttf (jedwali, cmap, glyf)
msingi/rasta.swa     -- kusawazisha Bezier + kujaza kwa nonzero winding
msingi/maktaba/      -- nakala zilizowekwa (vendored) za kumbukumbu.swa/
                        faili.swa/mfuatano.swa kutoka lugha-swa/swa
mtihani/             -- majaribio, ikiwemo onyesha_glyph.swa (chombo
                        cha kuonyesha glyph moja kama PGM)
```

## Kujenga na kujaribu

Inahitaji mkusanyaji wa [lugha-swa/swa](https://github.com/lugha-swa/swa)
(stage1, uliojengwa kwa mnyororo wake wa kawaida). Kutoka mzizi wa
saraka hii:

```sh
STAGE1=/njia/ya/stage1
MSULU=/njia/ya/msuluhishi

$MSULU mtihani/onyesha_glyph.swa > /tmp/zima.swa
$STAGE1 --exe /tmp/zima.swa > onyesha_glyph
chmod +x onyesha_glyph
./onyesha_glyph 65 herufi_A.pgm     # 65 = msimbo wa ASCII wa 'A'
convert herufi_A.pgm herufi_A.png    # zana ya kuthibitisha tu (ImageMagick)
```

Majaribio ya usomaji wa fonti (`mtihani/jaribio_ttf_*.swa`) yanathibitisha
thamani HALISI (si "haikuanguka" tu) dhidi ya fonti halisi iliyotajwa
hapo juu -- jenga na uendeshe kwa njia ile ile.

## Uthibitisho wa kuona

Herufi tano (L, O, A, B, S) -- zikifunika mistari iliyonyooka, shimo
moja, mashimo mawili, na curves safi -- zote zimechorwa kwa usahihi
na kuthibitishwa kwa macho dhidi ya fonti halisi wakati wa ujenzi wa
toleo hili la kwanza.
