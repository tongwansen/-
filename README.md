# -import requests

# 获取汇率数据的函数
def get_exchange_rate(api_key, base_currency, target_currency):
    url = f"https://v6.exchangerate-api.com/v6/{api_key}/latest/{base_currency}"
    response = requests.get(url)
    data = response.json()
    if response.status_code == 200:
        rate = data['conversion_rates'][target_currency]
        return rate
    else:
        print("Error fetching exchange rate data")
        return None

# 进行货币转换的函数
def convert_currency(amount, rate):
    return amount * rate

# 示例使用
api_key = "your_api_key_here"  # 在这里替换为你自己的API密钥
base_currency = "CNY"  # 基础货币
target_currency = "USD"  # 目标货币
amount = 100  # 要转换的金额

rate = get_exchange_rate(api_key, base_currency, target_currency)
if rate:
    converted_amount = convert_currency(amount, rate)
    print(f"{amount} {base_currency} = {converted_amount:.2f} {target_currency}")
else:
    print("无法获取汇率数据")

提供免费的汇率转换服务。
