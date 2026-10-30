# 🛒 Ecommerce Cartify

**A Mini E-Commerce Application for Practising Kubernetes Deployment Strategies**

Ecommerce Cartify is a lightweight, static e-commerce demo application created to demonstrate and practise different application deployment strategies using Docker and Kubernetes.

The main objective of this project is to understand how application updates are deployed in real-world environments, how new releases are introduced, how deployment issues are handled, and how we can roll back to a previous stable version.

This project uses a simple shopping application instead of a complex three-tier architecture so that learners can focus on Docker, Kubernetes, and deployment strategies without unnecessary application complexity.

---

## 🎯 Why Did We Create This Project?

In real-world DevOps environments, applications are updated frequently. Developers release new versions to introduce features, fix bugs, and improve application performance.

However, deploying a new version directly into production can introduce problems.

For example:
- A new release may contain bugs.
- Application availability may be affected during deployment.
- Some users may experience issues after an update.
- A newly deployed version may need to be rolled back.

To understand these real-world scenarios practically, we created Ecommerce Cartify with two different application releases.

- **Release 1.0:** Initial application version containing intentional bugs.
- **Release 2.0:** Improved application version with those bugs fixed.

Using these two releases, we can practise different deployment strategies and understand how DevOps engineers manage application updates.

---

## 🛍️ Application Features

Ecommerce Cartify provides a simple shopping experience with the following features:

- Display featured products.
- Add products to the shopping cart.
- Increase and decrease product quantities.
- Remove products from the cart.
- Calculate subtotal and discount.
- Display the final order amount.
- Simulate the checkout process.
- Responsive user interface.

**Note:** This is a frontend-only demonstration application. It does not use a backend, database, authentication system, or real payment gateway. Cart information is stored in browser memory and resets when the page is refreshed.

---

## 🏗️ Project Architecture

The application is built using simple web technologies and served through Nginx.

```text
                 Ecommerce Cartify
                         |
                 Static Web Application
                         |
                    Docker Image
                         |
                  Nginx Web Server
                         |
                 Kubernetes Deployment
                         |
             Different Deployment Strategies
                         |
       -----------------------------------------
       |             |            |            |
   Rolling        Blue-Green    Canary       Rollback
   Update         Deployment    Deployment
```

---

## 📁 Repository Structure

```text
ecommerce-cartify/
│
├── release-1/
│   ├── Dockerfile
│   └── index.html
│
├── release-2/
│   ├── Dockerfile
│   └── index.html
│
├── kubernetes/
│
└── README.md
```

### Directory Description

| Directory | Description |
|---|---|
| `release-1/` | Contains the initial application release (v1.0). |
| `release-2/` | Contains the improved application release (v2.0). |
| `kubernetes/` | Used to store Kubernetes deployment and service manifests. |
| `README.md` | Project documentation. |

---

## 🚀 Application Releases

### Release 1.0 – Initial Production Release

Release 1.0 represents the initial application deployment.

This version contains three intentional bugs:

1. **Duplicate Cart Entries:** Adding the same product multiple times creates separate cart entries instead of increasing the quantity.
2. **Incorrect Discount Calculation:** The application displays a 10% discount but calculates only 1%.
3. **Incorrect Cart Total:** The displayed total does not refresh correctly after cart quantity or product changes.

These issues are intentionally introduced to simulate a problematic production release.

### Release 2.0 – Bug Fixes and Improvements

Release 2.0 fixes the issues identified in Release 1.0.

Improvements include:

1. **Cart Management:** Adding the same product increases its existing quantity.
2. **Correct Discount:** The application calculates the correct 10% discount.
3. **Dynamic Cart Calculation:** The subtotal, discount, and total are recalculated whenever the cart changes.
4. **Additional Coupon Support:** Supports the demo coupon code `SAVE5` for an additional discount.

---

## 🐳 Docker Images

Both application releases are built as separate Docker images.

| Release | Docker Image |
|---|---|
| Release 1.0 | `ecommerce-cartify:v1.0` |
| Release 2.0 | `ecommerce-cartify:v2.0` |

### Build Release 1.0

```bash
cd release-1

docker build -t ecommerce-cartify:v1.0 .
```

### Build Release 2.0

```bash
cd release-2

docker build -t ecommerce-cartify:v2.0 .
```

### Verify Docker Images

```bash
docker images
```

