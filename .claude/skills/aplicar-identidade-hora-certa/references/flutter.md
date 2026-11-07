# Flutter — aplicação dos tokens

## Arquivos a criar
```
lib/theme/hc_colors.dart
lib/theme/hc_tokens.dart     (tamanhos, raios)
lib/theme/hc_theme.dart      (ThemeData)
lib/widgets/hc_buttons.dart  (TomeiButton, SecondaryButton, ExternalActionButton, SosButton)
lib/widgets/status_tag.dart
lib/widgets/hc_text_field.dart
assets/fonts/  Nunito-ExtraBold.ttf Nunito-Black.ttf AtkinsonHyperlegible-Regular.ttf AtkinsonHyperlegible-Bold.ttf
```

## pubspec.yaml
```yaml
flutter:
  fonts:
    - family: Nunito
      fonts:
        - asset: assets/fonts/Nunito-ExtraBold.ttf
          weight: 800
        - asset: assets/fonts/Nunito-Black.ttf
          weight: 900
    - family: AtkinsonHyperlegible
      fonts:
        - asset: assets/fonts/AtkinsonHyperlegible-Regular.ttf
        - asset: assets/fonts/AtkinsonHyperlegible-Bold.ttf
          weight: 700
```

## hc_colors.dart
```dart
import 'package:flutter/material.dart';

abstract final class HcColors {
  static const primary = Color(0xFF1D4F9F);
  static const primaryTint = Color(0xFFE4ECF8);
  static const primaryLine = Color(0xFFBBCDEC);
  static const background = Color(0xFFF5F8FD);
  static const surface = Color(0xFFFFFFFF);
  static const border = Color(0xFFD9E2F1);
  static const divider = Color(0xFFE6ECF6);
  static const ink = Color(0xFF1B2433);
  static const inkMuted = Color(0xFF4A5568);
  static const success = Color(0xFF1B7F45);
  static const successDark = Color(0xFF145C33);
  static const successTint = Color(0xFFDDF1E4);
  static const warning = Color(0xFFF5B335);
  static const warningTint = Color(0xFFFDE9BA);
  static const danger = Color(0xFFB8321F);
  static const dangerDark = Color(0xFF8E2414);
  static const dangerTint = Color(0xFFF9DCD6);
}
```

## hc_tokens.dart
```dart
abstract final class HcSize {
  static const touchMin = 64.0, buttonPrimary = 88.0, buttonSecondary = 72.0;
  static const gapButtons = 16.0, border = 3.0, tomeiStep = 6.0, screenPadding = 24.0;
}
abstract final class HcRadius {
  static const field = 16.0, button = 24.0, card = 32.0, cardCompact = 28.0, chip = 999.0;
}
```

## hc_theme.dart
```dart
import 'package:flutter/material.dart';
import 'hc_colors.dart';
import 'hc_tokens.dart';

const _head = 'Nunito', _body = 'AtkinsonHyperlegible';

ThemeData hcTheme() {
  final text = const TextTheme(
    displayLarge: TextStyle(fontFamily: _head, fontWeight: FontWeight.w900, fontSize: 40, height: 48 / 40, color: HcColors.ink),
    headlineMedium: TextStyle(fontFamily: _head, fontWeight: FontWeight.w800, fontSize: 32, height: 40 / 32, color: HcColors.ink),
    bodyLarge: TextStyle(fontFamily: _body, fontSize: 22, height: 32 / 22, color: HcColors.ink),
    bodyMedium: TextStyle(fontFamily: _body, fontSize: 18, height: 26 / 18, color: HcColors.inkMuted), // menor permitido
    labelLarge: TextStyle(fontFamily: _body, fontWeight: FontWeight.w700, fontSize: 28),
  );
  return ThemeData(
    useMaterial3: true,
    scaffoldBackgroundColor: HcColors.background,
    colorScheme: const ColorScheme.light(
      primary: HcColors.primary, onPrimary: Colors.white,
      secondary: HcColors.success, onSecondary: Colors.white,
      error: HcColors.danger, onError: Colors.white,
      surface: HcColors.surface, onSurface: HcColors.ink,
      outline: HcColors.border,
    ),
    textTheme: text,
    materialTapTargetSize: MaterialTapTargetSize.padded,
    cardTheme: CardThemeData(
      color: HcColors.surface, elevation: 0, margin: EdgeInsets.zero,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(HcRadius.card),
        side: const BorderSide(color: HcColors.border, width: HcSize.border),
      ),
    ),
    inputDecorationTheme: InputDecorationTheme(
      filled: true, fillColor: HcColors.surface,
      contentPadding: const EdgeInsets.symmetric(horizontal: 20, vertical: 18),
      labelStyle: text.bodyLarge, hintStyle: text.bodyMedium,
      enabledBorder: OutlineInputBorder(borderRadius: BorderRadius.circular(HcRadius.field),
          borderSide: const BorderSide(color: HcColors.border, width: HcSize.border)),
      focusedBorder: OutlineInputBorder(borderRadius: BorderRadius.circular(HcRadius.field),
          borderSide: const BorderSide(color: HcColors.primary, width: HcSize.border)),
    ),
    outlinedButtonTheme: OutlinedButtonThemeData(style: OutlinedButton.styleFrom(
      minimumSize: const Size.fromHeight(HcSize.buttonSecondary),
      foregroundColor: HcColors.primary, backgroundColor: HcColors.surface,
      side: const BorderSide(color: HcColors.primary, width: HcSize.border),
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(HcRadius.button)),
      textStyle: text.labelLarge,
    )),
  );
}
```

## Botão Tomei (degrau sólido)
```dart
class TomeiButton extends StatelessWidget {
  const TomeiButton({super.key, required this.onPressed, this.label = 'Tomei'});
  final VoidCallback? onPressed; final String label;
  @override
  Widget build(BuildContext context) => Semantics(
    button: true, label: label,
    child: Container(
      decoration: BoxDecoration(
        borderRadius: BorderRadius.circular(HcRadius.button),
        boxShadow: const [BoxShadow(color: HcColors.successDark, offset: Offset(0, HcSize.tomeiStep))], // sem blur
      ),
      child: FilledButton.icon(
        onPressed: onPressed,
        icon: const Icon(Icons.check_rounded, size: 36),
        label: Text(label),
        style: FilledButton.styleFrom(
          backgroundColor: HcColors.success, foregroundColor: Colors.white,
          minimumSize: const Size.fromHeight(HcSize.buttonPrimary),
          shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(HcRadius.button)),
          textStyle: Theme.of(context).textTheme.labelLarge,
        ),
      ),
    ),
  );
}
```
Os demais seguem o mesmo padrão: `SecondaryButton` = `OutlinedButton.icon` do tema; `ExternalActionButton` = `FilledButton` fundo `ink`; `SosButton` = `FilledButton` fundo `danger`, mínimo 64×64, ícone `warning_amber_rounded` + "SOS".

## StatusTag
```dart
enum HcStatus { tomado, proximo, atrasado }
class StatusTag extends StatelessWidget {
  const StatusTag(this.status, this.text, {super.key});
  final HcStatus status; final String text;
  @override
  Widget build(BuildContext context) {
    final (bg, fg, icon) = switch (status) {
      HcStatus.tomado => (HcColors.successTint, HcColors.successDark, Icons.check_rounded),
      HcStatus.proximo => (HcColors.warningTint, HcColors.ink, Icons.schedule_rounded),
      HcStatus.atrasado => (HcColors.dangerTint, HcColors.dangerDark, Icons.warning_amber_rounded),
    };
    return Container(
      padding: const EdgeInsets.symmetric(horizontal: 16, vertical: 8),
      decoration: BoxDecoration(color: bg, borderRadius: BorderRadius.circular(HcRadius.chip)),
      child: Row(mainAxisSize: MainAxisSize.min, children: [
        Icon(icon, color: fg, size: 22), const SizedBox(width: 8),
        Text(text, style: TextStyle(fontFamily: 'AtkinsonHyperlegible', fontWeight: FontWeight.w700, fontSize: 18, color: fg)),
      ]),
    );
  }
}
```

## Na aplicação
`MaterialApp(theme: hcTheme(), …)`. Depois troque `Color(0x…)`/`Colors.*`/`fontSize:` soltos nas telas por `HcColors`/`Theme.of(context).textTheme`.
