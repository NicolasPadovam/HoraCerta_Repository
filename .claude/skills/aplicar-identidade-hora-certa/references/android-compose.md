# Android — Kotlin + Jetpack Compose

## Arquivos
```
ui/theme/HcColors.kt   ui/theme/HcType.kt   ui/theme/HcDimens.kt   ui/theme/HcTheme.kt
ui/components/HcButtons.kt   ui/components/StatusTag.kt   ui/components/HcTextField.kt
res/font/nunito_extrabold.ttf nunito_black.ttf atkinson_regular.ttf atkinson_bold.ttf
```
(nomes em `res/font` só com minúsculas e `_`)

## HcColors.kt
```kotlin
object HcColors {
    val Primary = Color(0xFF1D4F9F); val PrimaryTint = Color(0xFFE4ECF8); val PrimaryLine = Color(0xFFBBCDEC)
    val Background = Color(0xFFF5F8FD); val Surface = Color(0xFFFFFFFF)
    val Border = Color(0xFFD9E2F1); val Divider = Color(0xFFE6ECF6)
    val Ink = Color(0xFF1B2433); val InkMuted = Color(0xFF4A5568)
    val Success = Color(0xFF1B7F45); val SuccessDark = Color(0xFF145C33); val SuccessTint = Color(0xFFDDF1E4)
    val Warning = Color(0xFFF5B335); val WarningTint = Color(0xFFFDE9BA)
    val Danger = Color(0xFFB8321F); val DangerDark = Color(0xFF8E2414); val DangerTint = Color(0xFFF9DCD6)
}
```

## HcDimens.kt
```kotlin
object HcDimens {
    val TouchMin = 64.dp; val ButtonPrimary = 88.dp; val ButtonSecondary = 72.dp
    val GapButtons = 16.dp; val Border = 3.dp; val TomeiStep = 6.dp; val ScreenPadding = 24.dp
    val RadiusField = 16.dp; val RadiusButton = 24.dp; val RadiusCard = 32.dp; val RadiusCardCompact = 28.dp
}
```

## HcType.kt
```kotlin
val Nunito = FontFamily(Font(R.font.nunito_extrabold, FontWeight.ExtraBold), Font(R.font.nunito_black, FontWeight.Black))
val Atkinson = FontFamily(Font(R.font.atkinson_regular, FontWeight.Normal), Font(R.font.atkinson_bold, FontWeight.Bold))

val HcTypography = Typography(
    displayLarge = TextStyle(fontFamily = Nunito, fontWeight = FontWeight.Black, fontSize = 40.sp, lineHeight = 48.sp),
    headlineMedium = TextStyle(fontFamily = Nunito, fontWeight = FontWeight.ExtraBold, fontSize = 32.sp, lineHeight = 40.sp),
    bodyLarge = TextStyle(fontFamily = Atkinson, fontSize = 22.sp, lineHeight = 32.sp),
    bodyMedium = TextStyle(fontFamily = Atkinson, fontSize = 18.sp, lineHeight = 26.sp), // menor permitido
    labelLarge = TextStyle(fontFamily = Atkinson, fontWeight = FontWeight.Bold, fontSize = 28.sp, lineHeight = 34.sp),
)
```

## HcTheme.kt
```kotlin
private val HcColorScheme = lightColorScheme(
    primary = HcColors.Primary, onPrimary = Color.White,
    secondary = HcColors.Success, onSecondary = Color.White,
    error = HcColors.Danger, onError = Color.White,
    background = HcColors.Background, onBackground = HcColors.Ink,
    surface = HcColors.Surface, onSurface = HcColors.Ink, onSurfaceVariant = HcColors.InkMuted,
    outline = HcColors.Border,
)
@Composable
fun HcTheme(content: @Composable () -> Unit) =
    MaterialTheme(colorScheme = HcColorScheme, typography = HcTypography, content = content)
```
Desative cores dinâmicas (Material You) se o projeto usa `dynamicLightColorScheme`.

## Botão Tomei (degrau sólido)
```kotlin
@Composable
fun TomeiButton(onClick: () -> Unit, modifier: Modifier = Modifier, text: String = "Tomei") {
    val shape = RoundedCornerShape(HcDimens.RadiusButton)
    Box(modifier.fillMaxWidth().padding(bottom = HcDimens.TomeiStep)) {
        Box(Modifier.matchParentSize().offset(y = HcDimens.TomeiStep).background(HcColors.SuccessDark, shape))
        Button(
            onClick = onClick, shape = shape,
            colors = ButtonDefaults.buttonColors(containerColor = HcColors.Success, contentColor = Color.White),
            modifier = Modifier.fillMaxWidth().heightIn(min = HcDimens.ButtonPrimary),
        ) {
            Icon(Icons.Rounded.Check, contentDescription = null, Modifier.size(36.dp))
            Spacer(Modifier.width(12.dp)); Text(text, style = MaterialTheme.typography.labelLarge)
        }
    }
}

@Composable
fun SecondaryButton(onClick: () -> Unit, text: String, icon: ImageVector, modifier: Modifier = Modifier) =
    OutlinedButton(
        onClick = onClick, shape = RoundedCornerShape(HcDimens.RadiusButton),
        border = BorderStroke(HcDimens.Border, HcColors.Primary),
        colors = ButtonDefaults.outlinedButtonColors(containerColor = HcColors.Surface, contentColor = HcColors.Primary),
        modifier = modifier.fillMaxWidth().heightIn(min = HcDimens.ButtonSecondary),
    ) { Icon(icon, null); Spacer(Modifier.width(12.dp)); Text(text, style = MaterialTheme.typography.labelLarge) }
```
`ExternalActionButton`: `Button` com `containerColor = HcColors.Ink`. `SosButton`: `Button` `containerColor = HcColors.Danger`, `Modifier.sizeIn(minWidth = 64.dp, minHeight = 64.dp)`, ícone `Icons.Rounded.Warning` + "SOS".

## StatusTag
```kotlin
enum class HcStatus { Tomado, Proximo, Atrasado }
@Composable
fun StatusTag(status: HcStatus, text: String) {
    val (bg, fg, icon) = when (status) {
        HcStatus.Tomado -> Triple(HcColors.SuccessTint, HcColors.SuccessDark, Icons.Rounded.Check)
        HcStatus.Proximo -> Triple(HcColors.WarningTint, HcColors.Ink, Icons.Rounded.Schedule)
        HcStatus.Atrasado -> Triple(HcColors.DangerTint, HcColors.DangerDark, Icons.Rounded.Warning)
    }
    Row(Modifier.background(bg, CircleShape).padding(horizontal = 16.dp, vertical = 8.dp),
        verticalAlignment = Alignment.CenterVertically) {
        Icon(icon, null, tint = fg, modifier = Modifier.size(22.dp)); Spacer(Modifier.width(8.dp))
        Text(text, color = fg, style = MaterialTheme.typography.bodyMedium.copy(fontWeight = FontWeight.Bold))
    }
}
```
(`Icons.Rounded.Schedule` exige `material-icons-extended`.)

## Na aplicação
Envolva o `setContent { HcTheme { … } }`. Troque `Color(0x…)`, `fontSize = …sp` e `Modifier.height(48.dp)` soltos pelos tokens.
