# Persönliche Website

Projekt: Multi-Personen-Home mit Subdomains und PHP-Template.

## Struktur
- `index.php` (Hauptseite)
- `styles.css`
- `includes/header.php` + `includes/footer.php`
- Subdomains: `alice`, `bob`, `chris` jeweils `index.php`

## Lokaler Workflow
1. `git pull`
2. `git add . && git commit -m "Update"`
3. `git push`

## Deployment auf Hosting
1. Domain-Root (`name.de`) auf `public_html`.
2. Subdomain `alice.name.de` auf `public_html/alice`, usw.
3. -> Alle `.php` Dateien im Webroot/Unterordner.

## HTTP -> HTTPS
1. Hosting-Panel: SSL/TLS-Management (Let's Encrypt / Automatisch)
2. Ziel: `https://name.de` / `https://alice.name.de`
3. Falls verfügbar: Leite HTTP nach HTTPS per Panel (häufig 1 Klick) oder `.htaccess`:

```
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

4. Test: Browser-URL muss `https://...` und grünes Schloss.

## Einmal prüfen
- `php -S 127.0.0.1:8000` im Ordner => lokaler Test
- Öffnen `http://127.0.0.1:8000`
- Kein Python/Node nötig.
