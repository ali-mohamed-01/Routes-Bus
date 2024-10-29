import pandas as pd

# تحميل البيانات من ملف Excel
file_path = 'Routes-Bus-Dashboard.xlsx'
data = pd.read_excel(file_path, sheet_name='Data Set', skiprows=4)  # تجاوز أول 4 صفوف للوصول إلى رؤوس الأعمدة

# تنظيف وتسمية الأعمدة
data.columns = ['Route', 'Sum of Riders', 'Total Buses', 'Total Trips', 'Avg Riders per Trip', 'Avg Riders per Bus']
data.dropna(inplace=True)

# إنشاء محتوى README
readme_content = f"""
# Routes Bus Dashboard

## مقدمة
يقدم هذا الملف تحليلًا لأعداد الركاب ومتوسط عددهم لكل رحلة عبر المسارات المختلفة باستخدام البيانات الواردة في ملف Excel.

## محتويات الملف
- **Data Set**: تحتوي على بيانات توضح مجموع عدد الركاب، وإجمالي الحافلات، وعدد الرحلات، ومتوسط الركاب لكل رحلة.
- **Dashboard**: ورقة عمل فارغة يمكن استخدامها لعرض النتائج بشكل بصري باستخدام الرسوم البيانية.

## الأعمدة الرئيسية
في ورقة "Data Set"، تشمل الأعمدة الرئيسية:
- **Route**: المسار أو الخط الخاص بالحافلة.
- **Sum of Riders**: مجموع عدد الركاب.
- **Total Buses**: إجمالي عدد الحافلات.
- **Total Trips**: إجمالي عدد الرحلات.
- **Avg Riders per Trip**: متوسط عدد الركاب لكل رحلة.
- **Avg Riders per Bus**: متوسط عدد الركاب لكل حافلة.

## تحليل البيانات
- **إجمالي عدد الركاب لكل مسار**:
  - أعلى مسار من حيث عدد الركاب هو: {data.groupby('Route')['Sum of Riders'].sum().idxmax()}
  - مجموع الركاب: {data['Sum of Riders'].sum()}
- **متوسط الركاب لكل رحلة**: {data['Avg Riders per Trip'].mean():.2f}

## الاستخدامات
يساعد هذا الملف في تحليل وتطوير خدمات النقل العام بناءً على بيانات الركاب والرحلات، مما يساعد في التخطيط لتحسين الكفاءة والخدمات.

## تعليمات الاستخدام
1. **تنظيف البيانات**: تأكد من تنظيم البيانات بشكل صحيح في ورقة "Data Set".
2. **إضافة الرسوم البيانية**: قم بإعداد الرسوم البيانية في ورقة "Dashboard" لتوضيح البيانات بصورة تفاعلية.
3. **تحديث البيانات**: يمكن تحديث الملف ببيانات جديدة للحصول على رؤى تحليلية حديثة.
"""

# حفظ ملف README
with open("README.md", "w", encoding="utf-8") as file:
    file.write(readme_content)

print("تم إنشاء ملف README.md بنجاح.")
