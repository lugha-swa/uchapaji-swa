<div align="center">
  <p>
    <a href="https://github.com/lugha-swa/uchapaji-swa">
      <picture>
        <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/lugha-swa/.github/main/rasilimali/mabango/uchapaji-swa-giza.png">
        <img width="100%" src="https://raw.githubusercontent.com/lugha-swa/.github/main/rasilimali/mabango/uchapaji-swa-mwanga.png" alt="uchapaji-swa — fonti za TrueType na kijazaji cha glyph, kwa Swa safi">
      </picture>
    </a>
  </p>

[Tovuti](https://lugha-swa.github.io) | [Swa](https://github.com/lugha-swa/swa) | [Jamii](https://lugha-swa.github.io/jamii.html)

<br>

<a href="https://github.com/lugha-swa/swa"><img src="https://img.shields.io/badge/imeandikwa_kwa-Swa-A34E14" alt="Imeandikwa kwa Swa"></a>
<img src="https://img.shields.io/badge/tegemezi_za_nje-hakuna-6B5E4A" alt="Hakuna tegemezi za nje">
<a href="#leseni"><img src="https://img.shields.io/badge/leseni-MIT%20%2F%20Apache--2.0-6B5E4A" alt="Leseni"></a>

</div>
<br>

**uchapaji-swa** husoma fonti za TrueType (`.ttf`) na kuchora glyph kuwa pikseli — kwa Swa safi, bila FreeType wala maktaba yoyote ya nje ya uchapaji. Ni kipande kati ya "kuweza kuchora maumbo" (DRM/KMS, kwenye [Dominion](https://github.com/Kandemark/dominion)) na "kuweza kuchora herufi halisi".

<p align="center">
  <img src="mifano/glyph_L.png" width="64" alt="L">
  <img src="mifano/glyph_O.png" width="64" alt="O">
  <img src="mifano/glyph_A.png" width="64" alt="A">
  <img src="mifano/glyph_B.png" width="64" alt="B">
  <img src="mifano/glyph_S.png" width="64" alt="S">
  <br>
  <sub>Glyph halisi za LiberationSans, zimechorwa na uchapaji-swa: mistari iliyonyooka (L), shimo moja (O, A), mashimo mawili (B), na curves (S).</sub>
</p>

## Anza

<details open>
<summary><b>Jenga na uendeshe</b></summary>
<br>

Mahitaji: mkusanyaji wa Swa (`bin/swa` kutoka `gharama/jenga.sh` ya [lugha-swa/swa](https://github.com/lugha-swa/swa)) na msuluhishi wa `husisha` (`gharama/msuluhishi.swa` ya hazina hiyo hiyo). Kutoka mzizi wa hazina hii:

```sh
SWA=/njia/ya/swa/bin/swa
MSULU=/njia/ya/msuluhishi

$MSULU mtihani/onyesha_glyph.swa > /tmp/zima.swa
$SWA --exe /tmp/zima.swa > onyesha_glyph && chmod +x onyesha_glyph
./onyesha_glyph 65 herufi_A.pgm     # 65 = msimbo wa ASCII wa 'A'
```

`herufi_A.pgm` ni picha ya kijivu; `magick herufi_A.pgm herufi_A.png` kuiona (ImageMagick, kwa kuthibitisha tu).

Majaribio ya usomaji (`mtihani/jaribio_ttf_*.swa`) hujengwa kwa njia ile ile, na yanathibitisha thamani **halisi** dhidi ya fonti halisi — si "haikuanguka" tu.

</details>

## Wigo

Imethibitishwa dhidi ya fonti halisi (`/usr/share/fonts/liberation/LiberationSans-Regular.ttf`), si data ya kubuni. Kila thamani ilihakikiwa kwanza kwa uchunguzi wa moja kwa moja wa faili kabla ya kuandika msimbo wa Swa.

| Kipengele | Hali |
|---|---|
| Mwelekeo wa jedwali, `head`, `maxp`, `loca`, `glyf` | imekamilika — baiti kwa baiti |
| `cmap` muundo 4 (BMP / Kilatini — inatosha kwa Kiswahili) | imekamilika |
| Glyph rahisi (simple glyphs) | imekamilika |
| Quadratic Bezier, ikiwemo pointi ya katikati iliyodokezwa kati ya off-curve mbili | imekamilika |
| Kujaza kwa scanline, kanuni ya **nonzero winding** | imekamilika — imethibitishwa na O (shimo 1) na B (mashimo 2) |
| Glyph za kiwanja (composite) | kazi ijayo |
| Anti-aliasing, hinting, kerning | kazi ijayo |
| Kuunganisha na onyesho la DRM/KMS la Dominion | kazi ijayo — leo inatoa bafa ya pikseli tu |

## Muundo wa hazina

| Njia | Maelezo |
|---|---|
| `msingi/ttf.swa` | msomaji wa `.ttf`: jedwali, `cmap`, `glyf` |
| `msingi/rasta.swa` | kusawazisha Bezier na kujaza kwa nonzero winding |
| `msingi/maktaba/` | nakala (vendored) za `kumbukumbu.swa`, `faili.swa`, `mfuatano.swa` kutoka lugha-swa/swa |
| `mtihani/` | majaribio, na `onyesha_glyph.swa` (glyph moja kama PGM) |
| `mifano/` | glyph zilizochorwa, zinazoonyeshwa hapo juu |

## Ikolojia

| Hazina | Maelezo |
|---|---|
| [lugha-swa/swa](https://github.com/lugha-swa/swa) | mkusanyaji na maktaba ya msingi |
| [lugha-swa/kawira](https://github.com/lugha-swa/kawira) | Swa kwenye ring 0 — kernel inayoanzisha, iliyoandikwa kwa Swa |
| [lugha-swa/uchapaji-swa](https://github.com/lugha-swa/uchapaji-swa) | msomaji wa TrueType na kijazaji cha glyph — hazina hii |
| [lugha-swa/tree-sitter-swa](https://github.com/lugha-swa/tree-sitter-swa) | sarufi ya Tree-sitter — rangi za sintaksia kwenye vihariri |
| [lugha-swa.github.io](https://github.com/lugha-swa/lugha-swa.github.io) | tovuti na mwongozo wa lugha |

## Leseni

Kwa chaguo lako, [Apache 2.0](LICENSE-APACHE) au [MIT](LICENSE-MIT).

<br>
<div align="center">
  <a href="https://github.com/lugha-swa"><img src="https://raw.githubusercontent.com/lugha-swa/.github/main/rasilimali/nembo/nembo-64.png" width="28" alt="lugha-swa"></a>
  <br>
  <sub>lugha-swa · Afrika ya Mashariki</sub>
</div>
