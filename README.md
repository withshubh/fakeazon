# Django E-commerce App with Cashfree Payments Integration

This project demonstrates how to integrate Cashfree Payments' payment gateway into a Django e-commerce application. It is intended for educational purposes and is not recommended for production use.

![demo1 (1)](https://github.com/withshubh/fakeazon/assets/25361949/60552227-a9d6-480d-9420-4085bc0c58f0)

![demo2](https://github.com/withshubh/fakeazon/assets/25361949/94e7b55d-321b-4dfa-b877-885efb535b67)


## Features

- **Landing Page**: Lists products fetched from the Fake Store API.
- **Cart Page**: Allows users to add, update, and remove products from the cart.
- **Payment Integration**: Uses Cashfree Payments' payment gateway to process orders.
- **Order Success Page**: Displays order details and redirects to the landing page after a successful payment.

## Getting Started

### Prerequisites

- Python 3.9+
- Django 4.2.13
- Cashfree Python SDK

### Installation

1. **Clone the repository**:

   ```sh
   git clone https://github.com/withshubh/fakeazon.git
   cd fakeazon
   ```

2. **Create and activate a virtual environment**:

   ```sh
   python -m venv myenv
   source myenv/bin/activate  # On Windows, use `myenv\Scripts\activate`
   ```

3. **Install the required packages**:

   ```sh
   pip install -r requirements.txt
   ```

4. **Set up the Django project**:

   ```sh
   python manage.py migrate
   python manage.py runserver
   ```

5. **Access the application**:

   Open your web browser and go to `http://localhost:8000`.

## Project Structure

- **shop/views.py**: Contains the views for the landing page, cart page, order creation, and order success page.
- **shop/templates/shop**: Contains the HTML templates for the landing page, cart page, and order success page.
- **shop/static/css/styles.css**: Contains the CSS styles for the application.

## Cashfree Payments Integration

### SDK Configuration

In `shop/views.py`, configure the Cashfree SDK with your **Client ID** and **Secret key**:

```python
from cashfree_pg.api_client import Cashfree

Cashfree.XClientId = 'YOUR_CLIENT_ID'
Cashfree.XClientSecret = 'YOUR_CLIENT_SECRET'
Cashfree.XEnvironment = Cashfree.SANDBOX  # Use `Cashfree.PRODUCTION` for production
```

### Creating an Order

The order creation process is handled in the create_order view. This view calculates the total amount from the cart, creates an order using the Cashfree SDK, and returns the payment session ID.

### Opening the Checkout Page

The payment session ID is used to open the Cashfree checkout page. This is done in the cart_page.html template using the Cashfree JavaScript SDK.

## Contributing

Contributions are welcome! Please read the [CONTRIBUTING.md](https://github.com/withshubh/fakeazon/blob/main/CONTRIBUTING.md) file for details on how to get started.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
