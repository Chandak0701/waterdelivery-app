import streamlit as st

st.title("🚰 Water Delivery App")
st.write("Order drinking water to your doorstep!")

water_sizes = ['1 Liter Bottle', '5 Liter Container', '20 Liter Can']

size = st.selectbox("Select Water Size", water_sizes)
quantity = st.number_input("How many?", min_value=1, step=1)

address = st.text_input("Enter delivery address")
delivery_time = st.selectbox("Preferred delivery time", ['ASAP', 'Morning', 'Afternoon', ' Evening'])

if st.button("Place Order"):
    if address:
        total = 0
        if size == '1 Liter Bottle':
            total = 20 * quantity
        elif size == '5 Liter Container':
            total = 80 * quantity
        elif size == '20 Liter Can':
            total = 250 * quantity

        st.success(f"✅ Your order has been placed.")
        st.write(f"*Size:* {size}")
        st.write(f"*Quantity:* {quantity}")
        st.write(f"*Delivery Address:* {address}")
        st.write(f"*Preferred delivery:* {delivery_time}")
        st.write(f"*Total Amount:* ₹{total}")
    else:
        st.error("❗ Please enter delivery address.")