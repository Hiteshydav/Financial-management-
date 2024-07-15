# Financial-management-import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt


data = {
    "Serial Number": [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50],
    "Name of Company": ["Reliance Inds.", "TCS", "HDFC Bank", "ITC", "H D F C", "Hind. Unilever", "Maruti Suzuki", "Infosys", "O N G C", "St Bk of India", "ICICI Bank", "Kotak Mah. Bank", "Coal India", "Larsen & Toubro", "I O C L", "Bharti Airtel", "Axis Bank", "NTPC", "Sun Pharma.Inds.", "Hind.Zinc", "Wipro", "HCL Technologies", "Vedanta", "Tata Motors", "UltraTech Cem.", "Asian Paints", "Power Grid Corpn", "B P C L", "IndusInd Bank", "Bajaj Fin.", "Bajaj Auto", "M & M", "HDFC Stand. Life", "Adani Ports", "Bajaj Finserv", "GAIL (India)", "Avenue Super.", "Titan Company", "JSW Steel", "Grasim Inds", "Tata Steel", "Eicher Motors", "Nestle India", "Godrej Consumer", "Yes Bank", "Hero Motocorp", "Motherson Sumi", "SBI Life Insuran", "General Insuranc", "Bharti Infra."],
    "Mar Cap - Crore": [583436.72, 563709.84, 482953.59, 320985.27, 289497.37, 288265.26, 263493.81, 248320.35, 239981.5, 232763.33, 203802.35, 199253.77, 192677.98, 180860.74, 178017.48, 167131.29, 136380.76, 135390.53, 134241.36, 133266.56, 131840.57, 126335.27, 122184.17, 117071.87, 113692.87, 108044.04, 102016.01, 98278, 97379.96, 94476.77, 88252.6, 88142.35, 87358.23, 81781.89, 79795.11, 78670.97, 74066.35, 73886, 73870.26, 73532.62, 73376.14, 73311.41, 73015.49, 71859.82, 71028.13, 69448.66, 68590.33, 67465, 66316.32, 61776.92],
    "Sales Qtr - Crore": [99810, 30904, 20581.27, 9772.02, 16840.51, 8590, 19283.2, 17794, 22995.88, 57014.08, 13665.35, 6390.71, 21643.28, 28747.45, 110666.93, 20318.6, 11721.55, 20774.37, 6653.23, 5922, 13669, 12809, 24361, 74156.07, 8019.24, 4260.52, 7506.95, 60616.36, 4286.78, 3540.63, 6369.34, 11577.78, 9734.9, 2688.85, 7665.4, 14414.34, 4094.82, 4274.84, 17861, 15291.42, 32464.14, 2269.01, 2601.46, 2630.3, 5070.3, 7305.49, 14397.85, 9569.97, 8557.68, None]
}

df = pd.DataFrame(data)


print(df.head())
print(df.describe())

print(df.isnull().sum())


corr = df['Mar Cap - Crore'].corr(df['Sales Qtr - Crore'])
print(f"Correlation between Market Capitalization and Quarterly Sales: {corr}")

plt.figure(figsize=(10, 6))
sns.scatterplot(data=df, x='Mar Cap - Crore', y='Sales Qtr - Crore')
plt.title('Market Capitalization vs Quarterly Sales')
plt.xlabel('Market Capitalization (Crores)')
plt.ylabel('Quarterly Sales (Crores)')
plt.show()

plt.figure(figsize=(10, 6))
sns.boxplot(data=df[['Mar Cap - Crore', 'Sales Qtr - Crore']])
plt.title('Boxplot of Market Capitalization and Quarterly Sales')
plt.show()

plt.figure(figsize=(10, 6))
sns.heatmap(df[['Mar Cap - Crore', 'Sales Qtr - Crore']].corr(), annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()
