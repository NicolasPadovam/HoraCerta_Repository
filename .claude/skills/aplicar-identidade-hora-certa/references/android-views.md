# Android — Views/XML (Java ou Kotlin)

Vale para projetos em **Java** com layouts XML (e Kotlin sem Compose). Os recursos XML são iguais; só os trechos de código mudam de linguagem.

## Arquivos
```
res/values/colors.xml   res/values/dimens.xml   res/values/themes.xml   res/values/styles_hc.xml
res/font/nunito.xml  atkinson.xml  (+ nunito_extrabold.ttf nunito_black.ttf atkinson_regular.ttf atkinson_bold.ttf)
res/drawable/bg_btn_tomei.xml  bg_btn_secondary.xml  bg_btn_sos.xml  bg_card.xml  bg_field.xml  bg_tag_*.xml
```

## colors.xml
```xml
<resources>
    <color name="hc_primary">#1D4F9F</color>
    <color name="hc_primary_tint">#E4ECF8</color>
    <color name="hc_primary_line">#BBCDEC</color>
    <color name="hc_background">#F5F8FD</color>
    <color name="hc_surface">#FFFFFF</color>
    <color name="hc_border">#D9E2F1</color>
    <color name="hc_divider">#E6ECF6</color>
    <color name="hc_ink">#1B2433</color>
    <color name="hc_ink_muted">#4A5568</color>
    <color name="hc_success">#1B7F45</color>
    <color name="hc_success_dark">#145C33</color>
    <color name="hc_success_tint">#DDF1E4</color>
    <color name="hc_warning">#F5B335</color>
    <color name="hc_warning_tint">#FDE9BA</color>
    <color name="hc_danger">#B8321F</color>
    <color name="hc_danger_dark">#8E2414</color>
    <color name="hc_danger_tint">#F9DCD6</color>
</resources>
```

## dimens.xml
```xml
<resources>
    <dimen name="hc_touch_min">64dp</dimen>
    <dimen name="hc_button_primary">88dp</dimen>
    <dimen name="hc_button_secondary">72dp</dimen>
    <dimen name="hc_gap_buttons">16dp</dimen>
    <dimen name="hc_border">3dp</dimen>
    <dimen name="hc_tomei_step">6dp</dimen>
    <dimen name="hc_screen_padding">24dp</dimen>
    <dimen name="hc_radius_field">16dp</dimen>
    <dimen name="hc_radius_button">24dp</dimen>
    <dimen name="hc_radius_card">32dp</dimen>
    <dimen name="hc_text_display">40sp</dimen>
    <dimen name="hc_text_title">32sp</dimen>
    <dimen name="hc_text_body">22sp</dimen>
    <dimen name="hc_text_button">28sp</dimen>
    <dimen name="hc_text_support">18sp</dimen>
</resources>
```

## res/font/nunito.xml (família)
```xml
<font-family xmlns:app="http://schemas.android.com/apk/res-auto">
    <font app:fontStyle="normal" app:fontWeight="800" app:font="@font/nunito_extrabold"/>
    <font app:fontStyle="normal" app:fontWeight="900" app:font="@font/nunito_black"/>
</font-family>
```
`atkinson.xml` igual, com 400 → `atkinson_regular` e 700 → `atkinson_bold`.

## themes.xml
```xml
<style name="Theme.HoraCerta" parent="Theme.Material3.Light.NoActionBar">
    <item name="colorPrimary">@color/hc_primary</item>
    <item name="colorOnPrimary">@android:color/white</item>
    <item name="colorSecondary">@color/hc_success</item>
    <item name="colorError">@color/hc_danger</item>
    <item name="android:colorBackground">@color/hc_background</item>
    <item name="android:windowBackground">@color/hc_background</item>
    <item name="colorSurface">@color/hc_surface</item>
    <item name="colorOnSurface">@color/hc_ink</item>
    <item name="colorOutline">@color/hc_border</item>
    <item name="android:fontFamily">@font/atkinson</item>
    <item name="fontFamily">@font/atkinson</item>
    <item name="android:textColor">@color/hc_ink</item>
    <item name="materialButtonStyle">@style/HC.Button.Secondary</item>
</style>
```
Aplique em `AndroidManifest.xml`: `android:theme="@style/Theme.HoraCerta"`. Se o projeto usa `Theme.AppCompat`, mantenha o pai e use os mesmos itens.

## styles_hc.xml
```xml
<resources>
    <style name="HC.Text.Display"><item name="fontFamily">@font/nunito</item><item name="android:textFontWeight">900</item><item name="android:textSize">@dimen/hc_text_display</item><item name="android:textColor">@color/hc_ink</item></style>
    <style name="HC.Text.Title"><item name="fontFamily">@font/nunito</item><item name="android:textFontWeight">800</item><item name="android:textSize">@dimen/hc_text_title</item><item name="android:textColor">@color/hc_ink</item></style>
    <style name="HC.Text.Body"><item name="fontFamily">@font/atkinson</item><item name="android:textSize">@dimen/hc_text_body</item><item name="android:lineSpacingExtra">10sp</item><item name="android:textColor">@color/hc_ink</item></style>
    <style name="HC.Text.Support"><item name="fontFamily">@font/atkinson</item><item name="android:textSize">@dimen/hc_text_support</item><item name="android:textColor">@color/hc_ink_muted</item></style>

    <style name="HC.Button.Base" parent="Widget.Material3.Button">
        <item name="android:minHeight">@dimen/hc_button_secondary</item>
        <item name="android:textSize">@dimen/hc_text_button</item>
        <item name="fontFamily">@font/atkinson</item>
        <item name="android:textStyle">bold</item>
        <item name="android:textAllCaps">false</item>
        <item name="cornerRadius">@dimen/hc_radius_button</item>
        <item name="iconSize">32dp</item>
        <item name="iconPadding">12dp</item>
    </style>
    <style name="HC.Button.Tomei" parent="HC.Button.Base">
        <item name="android:minHeight">@dimen/hc_button_primary</item>
        <item name="backgroundTint">@null</item>
        <item name="android:background">@drawable/bg_btn_tomei</item>
        <item name="android:textColor">@android:color/white</item>
        <item name="icon">@drawable/ic_check</item>
        <item name="iconTint">@android:color/white</item>
    </style>
    <style name="HC.Button.Secondary" parent="HC.Button.Base">
        <item name="backgroundTint">@color/hc_surface</item>
        <item name="android:textColor">@color/hc_primary</item>
        <item name="strokeColor">@color/hc_primary</item>
        <item name="strokeWidth">@dimen/hc_border</item>
        <item name="iconTint">@color/hc_primary</item>
    </style>
    <style name="HC.Button.External" parent="HC.Button.Base">
        <item name="backgroundTint">@color/hc_ink</item>
        <item name="android:textColor">@android:color/white</item>
    </style>
    <style name="HC.Button.Sos" parent="HC.Button.Base">
        <item name="backgroundTint">@color/hc_danger</item>
        <item name="android:textColor">@android:color/white</item>
        <item name="android:minWidth">@dimen/hc_touch_min</item>
        <item name="android:minHeight">@dimen/hc_touch_min</item>
        <item name="android:textSize">@dimen/hc_text_support</item>
        <item name="icon">@drawable/ic_warning</item>
        <item name="iconTint">@android:color/white</item>
    </style>
</resources>
```

## bg_btn_tomei.xml (degrau sólido de 6dp)
```xml
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:top="6dp">
        <shape><solid android:color="@color/hc_success_dark"/><corners android:radius="@dimen/hc_radius_button"/></shape>
    </item>
    <item android:bottom="6dp">
        <shape><solid android:color="@color/hc_success"/><corners android:radius="@dimen/hc_radius_button"/></shape>
    </item>
</layer-list>
```
Outros drawables: `bg_card.xml` = shape surface + stroke 3dp `hc_border` + raio 32dp; `bg_field.xml` = selector (focado: stroke `hc_primary`; normal: `hc_border`) raio 16dp; `bg_tag_tomado/proximo/atrasado.xml` = shape com raio 999dp e as cores *Tint*.

## Uso no layout
```xml
<com.google.android.material.button.MaterialButton
    style="@style/HC.Button.Tomei"
    android:layout_width="match_parent" android:layout_height="wrap_content"
    android:text="@string/tomei"/>
```

## StatusTag (Java)
```java
public final class StatusTag {
    public enum Status { TOMADO, PROXIMO, ATRASADO }
    public static void apply(TextView v, Status s, String text) {
        int bg, fg, icon;
        switch (s) {
            case TOMADO:  bg = R.drawable.bg_tag_tomado;   fg = R.color.hc_success_dark; icon = R.drawable.ic_check;    break;
            case PROXIMO: bg = R.drawable.bg_tag_proximo;  fg = R.color.hc_ink;          icon = R.drawable.ic_schedule; break;
            default:      bg = R.drawable.bg_tag_atrasado; fg = R.color.hc_danger_dark;  icon = R.drawable.ic_warning;  break;
        }
        int color = ContextCompat.getColor(v.getContext(), fg);
        v.setText(text);
        v.setBackgroundResource(bg);
        v.setTextColor(color);
        v.setCompoundDrawablesRelativeWithIntrinsicBounds(icon, 0, 0, 0);
        TextViewCompat.setCompoundDrawableTintList(v, ColorStateList.valueOf(color));
    }
}
```
Em Kotlin, mesma lógica com `when`.

## Na aplicação
Procure `android:textColor="#…"`, `android:textSize="…sp"`, `android:background="#…"` e `layout_height="48dp"` nos layouts e troque por `@color/hc_*`, estilos `HC.*` e `@dimen/hc_*`.
