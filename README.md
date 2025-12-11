# Pages Légales Publiques - Budget Pro

## 📋 Contexte

Google Play Store exige que les URL de Privacy Policy et Terms of Service soient **publiquement accessibles** sans authentification.

Le problème actuel : Le panel admin sur Vercel (`https://admin-panel-bvy3f0reo-mimbe237s-projects.vercel.app/`) a la protection Vercel SSO activée, ce qui bloque l'accès public aux routes `/privacy` et `/terms`.

## ✅ Solution : Pages HTML Statiques

Les fichiers `privacy.html` et `terms.html` dans ce dossier sont des versions statiques prêtes à être hébergées publiquement.

### Contenu
- **privacy.html** : Privacy Policy complète (GDPR compliant)
- **terms.html** : Terms of Service complets

## 🚀 Options d'Hébergement

### Option 1 : GitHub Pages (RECOMMANDÉ - GRATUIT)

**Avantages** : Gratuit, rapide, HTTPS automatique, pas de configuration complexe

**Instructions :**

1. **Créer un dépôt GitHub public :**
```bash
cd /Users/macbook/budget/public_legal
git init
git add .
git commit -m "Initial commit - Legal pages"
```

2. **Créer un repo sur GitHub :**
   - Nom : `budgetpro-legal` (ou similaire)
   - Type : **Public**
   - Ne pas initialiser avec README

3. **Pusher le code :**
```bash
git remote add origin https://github.com/VOTRE_USERNAME/budgetpro-legal.git
git branch -M main
git push -u origin main
```

4. **Activer GitHub Pages :**
   - Settings → Pages
   - Source : Deploy from branch
   - Branch : main / (root)
   - Save

5. **URLs finales :**
```
https://VOTRE_USERNAME.github.io/budgetpro-legal/privacy.html
https://VOTRE_USERNAME.github.io/budgetpro-legal/terms.html
```

---

### Option 2 : Firebase Hosting (GRATUIT)

**Avantages** : Déjà configuré Firebase, même domaine que l'app

**Instructions :**

1. **Créer la structure :**
```bash
cd /Users/macbook/budget
mkdir -p public/legal
cp public_legal/*.html public/legal/
```

2. **Déployer :**
```bash
firebase deploy --only hosting
```

3. **URLs finales :**
```
https://budget-pro-8e46f.web.app/legal/privacy.html
https://budget-pro-8e46f.web.app/legal/terms.html
```

---

### Option 3 : Netlify Drop (GRATUIT)

**Avantages** : Le plus rapide (drag & drop), pas de compte nécessaire

**Instructions :**

1. **Ouvrir :** https://app.netlify.com/drop

2. **Glisser-déposer** le dossier `public_legal`

3. **URLs générées automatiquement :**
```
https://random-name.netlify.app/privacy.html
https://random-name.netlify.app/terms.html
```

4. **Optionnel :** Créer un compte pour personnaliser le nom de domaine

---

### Option 4 : Vercel Public Project (GRATUIT)

**Avantages** : Déjà sur Vercel, HTTPS, build automatique

**Instructions :**

1. **Créer un nouveau projet Vercel :**
   - Dashboard Vercel → Add New → Project
   - Import le dossier `public_legal`
   - **IMPORTANT :** NE PAS activer Vercel SSO sur ce projet

2. **Configuration :**
   - Build Command : (laisser vide)
   - Output Directory : `./`
   - Framework Preset : Other

3. **URLs finales :**
```
https://budgetpro-legal.vercel.app/privacy.html
https://budgetpro-legal.vercel.app/terms.html
```

---

### Option 5 : Désactiver Vercel SSO (pour /privacy et /terms uniquement)

**Avantages** : Garde tout sur le même domaine

**Instructions :**

1. **Dashboard Vercel :**
   - Ouvrir le projet `admin-panel-bvy3f0reo`
   - Settings → Deployment Protection
   - Vercel Authentication → Configure

2. **Exclure les routes :**
   Ajouter dans `vercel.json` :
```json
{
  "framework": "nextjs",
  "buildCommand": "npm run build",
  "installCommand": "npm install",
  "outputDirectory": ".next",
  "routes": [
    {
      "src": "/(privacy|terms)",
      "headers": { "x-vercel-protection-bypass": "true" }
    }
  ]
}
```

3. **Redéployer :**
```bash
cd /Users/macbook/budget/admin_panel
git add vercel.json
git commit -m "Public access for legal pages"
git push
```

**Note :** Cette méthode peut ne pas fonctionner avec Vercel SSO (nécessite désactivation complète de la protection)

---

## 📝 Recommandation

**Option 1 (GitHub Pages)** est la plus simple et la plus fiable pour les besoins du Play Store.

**Temps estimé :** 5 minutes

**Aucun risque** de bloquer l'accès admin au panel.

---

## 🔗 URLs à Soumettre au Play Store

Une fois hébergé, noter les URLs pour le formulaire Play Store :

```
Privacy Policy: https://...
Terms of Service: https://...
```

Ces URLs doivent être :
- ✅ Accessibles publiquement (sans login)
- ✅ HTTPS
- ✅ Contenu complet et lisible
- ✅ Pas de redirections

---

## 📄 Contenu des Pages

Les deux fichiers HTML incluent :

**Privacy Policy :**
- Data Collection
- Data Usage
- Security
- Data Sharing
- User Rights (GDPR)
- Cookies & Tracking
- Children
- Policy Changes
- Contact Info

**Terms of Service :**
- Acceptance of Terms
- Service Description
- Account Creation
- Acceptable Use
- Intellectual Property
- Limitation of Liability
- Data & Privacy
- Payment & Subscriptions
- Account Termination
- Changes to Terms
- Governing Law
- Contact Info

---

## 🚨 Important

- **NE PAS** supprimer ces fichiers après hébergement
- **NE PAS** ajouter d'authentification sur ces URLs
- **NE PAS** rediriger vers d'autres pages
- **VÉRIFIER** que les URLs sont accessibles en navigation privée

---

**Créé le :** 11 Décembre 2025  
**Projet :** Budget Pro by BEONWEB  
**Contact :** support@budgetpro.cm
