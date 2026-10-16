# Facebook Auto Post SaaS Tool - Installation Guide

This guide provides step-by-step instructions to deploy your Facebook Auto Post SaaS tool using **Vercel** or **Render** for free hosting, and **Supabase** for a free database.

---

## 🛠️ Step 1: Prepare Your Code on GitHub

To ensure you have full, lifetime control over your code without history tracking from previous developers:
1. **Create a New Repository:** Log in to [GitHub](https://github.com/) and create a new **Public** repository without checking the "Add a README file" option.
2. **Upload Files:** Click on `uploading an existing file` on the quick setup page.
3. **Drag & Drop:** Select all files and folders inside your local workspace (ensure no old `.git` folders exist if downloaded directly as a ZIP) and upload them.
4. **Commit:** Click `Commit changes`.

---

## 🗄️ Step 2: Set Up Supabase Free Database

1. Go to [Supabase](https://supabase.com/) and sign up or sign in using your GitHub account.
2. Click **New Project** and configure:
   - **Name:** Choose a name (e.g., `fb-autopilot-db`).
   - **Database Password:** Click `Generate a password`. **Copy and save this password safely.**
   - **Pricing Plan:** Select the **Free** tier.
3. Click **Create new project** and wait 1–2 minutes for setup.
4. Go to **Project Settings (⚙️ icon at the bottom-left)** > **API** and copy:
   - **Project URL:** Save this as your database link.
   - **`service_role` Key:** Click *Reveal* and copy the secret token.
5. **Run the Database Schema:**
   - Click **SQL Editor** (`>_` icon on the left menu).
   - Click **New Query** to open a blank editor.
   - Copy the entire contents of the `supabase/schema.sql` file from your project code.
   - Paste it into the editor box and click **Run**. A `Success` message will confirm your database tables are ready.

---

## 🚀 Step 3: Deploy the Web Tool (Choose Option A or B)

### Option A: Free Hosting on Vercel (Recommended)
1. Go to [Vercel](https://vercel.com/) and log in using **Continue with GitHub**.
2. Click **Add New > Project**.
3. Locate your newly uploaded repository and click **Import**.
4. Expand the **Environment Variables** section. Add the following 4 keys carefully:
   - **`NEXT_PUBLIC_SUPABASE_URL`** (Type: Change from *Secret* to *Config* if it gives validation warnings)
     - *Value:* `https://your-project-id.supabase.co`
   - **`SUPABASE_SERVICE_ROLE_KEY`** (Type: *Secret*)
     - *Value:* (Your secret `service_role` key copied from Supabase)
   - **`ADMIN_PASSWORD`** (Type: *Secret*)
     - *Value:* (Create a custom strong password to log into your tool's dashboard)
   - **`SESSION_SECRET`** (Type: *Secret*)
     - *Value:* (Any long random string of letters or numbers, e.g., `mysecretstring12345`)
5. Click **Deploy**. Vercel will build your application in a minute and provide a live production domain URL.

### Option B: Free Hosting on Render
1. Go to [Render](https://render.com/) and sign up or log in with GitHub.
2. Click **New +** and select **Web Service**.
3. Connect your GitHub account, find your repository, and click **Connect**.
4. Set the configuration details:
   - **Runtime:** `Node`
   - **Build Command:** `npm run build` or `yarn build` (depending on your project configuration)
   - **Start Command:** `npm run start` or `yarn start`
5. Click **Advanced** to open the Environment Variables section and add the exact same 4 variables listed above:
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `SUPABASE_SERVICE_ROLE_KEY`
   - `ADMIN_PASSWORD`
   - `SESSION_SECRET`
6. Click **Create Web Service**. Render will deploy your application and give you a live `.onrender.com` URL.

---

## 🌐 Step 4: Configure the Facebook Developer App

1. Go to [Facebook Developers](https://developers.facebook.com/) and log in.
2. Click **Create App** and select **Manage everything on your page** or Content Management use case.
3. Under **Use Cases > Customize**, add these permissions:
   - `pages_manage_posts`
   - `pages_read_engagement`
4. Go to **App Settings > Basic**:
   - Add your Vercel or Render production domain name to the **App Domains** field.
   - Enter your full URL in the **Privacy Policy URL** field.
   - Click **Add Platform** at the bottom, select **Website**, and input your full application site URL. Save your changes.
5. In the left panel, add the **Facebook Login** product and navigate to its settings:
   - Copy the **Redirect URL** from your live web tool's dashboard settings panel.
   - Paste it inside Facebook's **Valid OAuth Redirect URIs** field and click save.
6. Copy your **App ID** and **App Secret** from the Basic settings window, paste them into your tool's settings dashboard, and hit **Save Credentials**.
7. Connect your Facebook Page, generate or schedule your content, and let the autopilot post seamlessly for free!

<br><br>

========================================================================

<br><br>

# ফেসবুক অটো পোস্ট SaaS টুল - ইন্সটলেশন গাইড

ভবিষ্যতে কোনো ঝামেলা ছাড়াই আপনার ফেসবুক অটো পোস্ট SaaS টুলটি সম্পূর্ণ ফ্রিতে সেটআপ করার জন্য নিচে **Vercel** এবং **Render** উভয় হোস্টিং সিস্টেমসহ ধাপে ধাপে বাংলা গাইড দেওয়া হলো।

---

## 🛠️ ধাপ ১: GitHub-এ কোড রেডি করা

কোডের ওপর আপনার আজীবন নিয়ন্ত্রণ রাখতে এবং পেছনের ডেভেলপারদের হিস্ট্রি সম্পূর্ণ মুছে ফেলতে নিচের নিয়মটি ফলো করুন:
1. **নতুন রিপোজিটরি তৈরি:** [GitHub](https://github.com/)-এ লগইন করে একটি নতুন **Public** রিপোজিটরি তৈরি করুন (তৈরি করার সময় `Add a README file`-এ টিক দেবেন না)।
2. **ফাইল আপলোড:** কুইক সেটিংস পেজ থেকে `uploading an existing file` লিঙ্কে ক্লিক করুন।
3. **ড্র্যাগ অ্যান্ড ড্রপ:** আপনার কম্পিউটারে ডাউনলোড করা ফোল্ডারের ভেতরের সব ফাইল ও সাব-ফোল্ডার একসাথে সিলেক্ট করে আপলোড বক্সে ছেড়ে দিন। 
4. **কমিট:** নিচে থাকা `Commit changes` বাটনে ক্লিক করুন।

---

## 🗄️ ধাপ ২: Supabase-এ ফ্রি ডাটাবেজ সেটআপ

1. [Supabase](https://supabase.com/) ওয়েবসাইটে গিয়ে আপনার GitHub অ্যাকাউন্ট দিয়ে লগইন করুন।
2. **New Project**-এ ক্লিক করে নিচের মতো ফর্ম পূরণ করুন:
   - **Name:** প্রজেক্টের নাম দিন (যেমন: `fb-autopilot-db`)।
   - **Database Password:** পাসওয়ার্ড জেনারেট করে সেটি নোটপ্যাডে সুরক্ষিতভাবে সেভ করে রাখুন।
   - **Pricing Plan:** নিশ্চিত করুন এটি যেন **Free** প্ল্যান সিলেক্ট করা থাকে।
3. **Create new project** বাটনে ক্লিক করুন এবং ১-২ মিনিট অপেক্ষা করুন।
4. প্রজেক্ট রেডি হলে বাম পাশের নিচে থাকা **Project Settings (⚙️ আইকন)** > **API** অপশনে যান এবং এই ২টি কোড নোটপ্যাডে কপি করে রাখুন:
   - **Project URL** (এটি আপনার ডাটাবেজ লিঙ্ক)
   - **`service_role` Key** (Reveal বাটনে ক্লিক করে সিক্রেট টোকেনটি কপি করুন)
5. **SQL Schema রান করা (বাধ্যতামূলক):**
   - বাম পাশের মেনু থেকে **SQL Editor** (`>_` আইকন) অপশনে যান।
   - **New Query**-তে ক্লিক করে একটি খালি বক্স খুলুন।
   - আপনার কোড ফাইলের ভেতরে থাকা `supabase/schema.sql` ফাইলের পুরো কোডটি কপি করে এনে এখানে পেস্ট করুন।
   - নিচে থাকা **Run** বাটনে ক্লিক করুন। নিচে `Success` লেখা আসলে বুঝবেন টেবিল তৈরি কমপ্লিট।

---

## 🚀 ধাপ ৩: ওয়েব টুলটি লাইভ করা (যেকোনো ১টি পদ্ধতি বেছে নিন)

### পদ্ধতি ক: Vercel হোস্টিংয়ের মাধ্যমে (অনুমোদিত ও সহজ)
1. [Vercel](https://vercel.com/) ওয়েবসাইটে যান এবং **Continue with GitHub** দিয়ে লগইন করুন।
2. ড্যাশবোর্ড থেকে **Add New > Project**-এ ক্লিক করুন।
3. আপনার গিটহাবের `facebook-auto-bot` রিপোজিটরিটির পাশে থাকা **Import** বাটনে ক্লিক করুন।
4. প্রজেক্ট কনফিগারেশন পেজে **Environment Variables** সেকশনটি ওপেন করে নিচের ৪টি কি (Key) এবং ভ্যালু (Value) যোগ করুন:
   - **`NEXT_PUBLIC_SUPABASE_URL`** (Type: এডিট করার সময় কোনো সমস্যা বা ওয়ার্নিং দিলে এটি *Secret* থেকে পরিবর্তন করে *Config* সিলেক্ট করে দেবেন)
     - *Value:* `https://your-project-id.supabase.co`
   - **`SUPABASE_SERVICE_ROLE_KEY`** (Type: *Secret*)
     - *Value:* (Supabase থেকে কপি করা সিক্রেট `service_role` কী)
   - **`ADMIN_PASSWORD`** (Type: *Secret*)
     - *Value:* (বটের ড্যাশবোর্ডে লগইন করার জন্য আপনার নিজের পছন্দমতো পাসওয়ার্ড)
   - **`SESSION_SECRET`** (Type: *Secret*)
     - *Value:* (যেকোনো র্যান্ডম দীর্ঘ লেখা বা সংখ্যা, যেমন: `mysecretstring12345`)
5. সব ভেরিয়েবল অ্যাড করা হয়ে গেলে নিচের **Deploy** বাটনে ক্লিক করুন। ১ মিনিটের মধ্যে Vercel আপনাকে একটি লাইভ ডোমেইন লিঙ্ক (URL) দিয়ে দেবে।

### পদ্ধতি খ: Render হোস্টিংয়ের মাধ্যমে (বিকল্প ফ্রি ব্যবস্থা)
1. [Render](https://render.com/) ওয়েবসাইটে যান এবং GitHub দিয়ে সাইন আপ বা লগইন করুন।
2. ড্যাশবোর্ড থেকে ওপরে থাকা **New +** বাটনে ক্লিক করে **Web Service** সিলেক্ট করুন।
3. আপনার GitHub অ্যাকাউন্টটি কানেক্ট করে আপনার বটের রিপোজিটরিটির পাশে থাকা **Connect** বাটনে ক্লিক করুন।
4. কনফিগারেশন পেজে নিচের সেটিংসগুলো দিন:
   - **Runtime:** `Node`
   - **Build Command:** `npm run build` অথবা `yarn build`
   - **Start Command:** `npm run start` अथवा `yarn start`
5. পেজের নিচের দিকে থাকা **Advanced** অপশনে ক্লিক করে **Add Environment Variable**-এ যান এবং ওপরে উল্লেখিত ৪টি ভেরিয়েবল হুবহু একই নিয়মে (Key এবং Value হিসেবে) যোগ করুন।
6. সবশেষে **Create Web Service** বাটনে ক্লিক করুন। Render প্রজেক্টটি বিল্ড করে আপনাকে একটি ফ্রি লাইভ `.onrender.com` লিঙ্ক দেবে।

---

## 🌐 ধাপ ৪: Facebook Meta App কনফিগারেশন

1. [Facebook Developers](https://developers.facebook.com/) পোর্টালে লগইন করে **Create App**-এ ক্লিক করুন।
2. Use Case হিসেবে **Manage everything on your page** সিলেক্ট করে অ্যাপটি তৈরি করুন।
3. অ্যাপের ভেতরে বাম পাশের **Use Cases > Customize**-এ গিয়ে নিচের পারমিশন দুটি অন করুন:
   - `pages_manage_posts`
   - `pages_read_engagement`
4. অ্যাপের **App Settings > Basic**-এ যান:
   - **App Domains:** আপনার Vercel বা Render সাইটের ডোমেইনটি বসান (http/https ছাড়া)।
   - **Privacy Policy URL:** আপনার লাইভ ওয়েবসাইটের সম্পূর্ণ লিঙ্কটি (https সহ) পেস্ট করুন।
   - পেজের নিচে **Add Platform**-এ ক্লিক করে **Website** সিলেক্ট করুন এবং সাইটের বক্সে আপনার অ্যাপের সম্পূর্ণ লিঙ্কটি দিয়ে `Save Changes` করুন।
5. বাম পাশের মেনু থেকে **Facebook Login > Settings**-এ যান:
   - আপনার বটের লাইভ ড্যাশবোর্ডের Settings থেকে **Redirect URL**-টি কপি করে আনুন।
   - সেটি ফেসবুক অ্যাপের **Valid OAuth Redirect URIs** বক্সে পেস্ট করে সেভ করুন।
6. অ্যাপের Basic সেটিংস থেকে **App ID** এবং **App Secret** কপি করে আপনার বটের ড্যাশবোর্ডের সেটিংসে বসিয়ে **Save Credentials** দিন।
7. এবার ড্যাশবোর্ড থেকে পেজ কানেক্ট করে ফ্রিতে আজীবনের জন্য অটো পাইলট পোস্ট এনজয় করুন!
