# Lab 5

Pliki:
- namespaces.yaml — tworzy ns-dev i ns-prod
- ns-dev-limitrange.yaml — LimitRange dla ns-dev (default 200m/256Mi, max 200m/256Mi)
- resourcequotas.yaml — ResourceQuota dla ns-dev (pods=10, CPU=2, MEM=2560Mi) oraz ns-prod (2x)
- no-test-deployment.yaml — deployment który żąda CPU 500m/512Mi (ma zostać odrzucony)
- yes-test-deployment.yaml — deployment działający (100m/128Mi request)
- zero-test-deployment.yaml — deployment bez zasobów (LimitRange przypisuje defaulty)

Instrukcja:
1. kubectl apply -f namespaces.yaml
2. kubectl apply -f ns-dev-limitrange.yaml
3. kubectl apply -f resourcequotas.yaml
4. kubectl apply -f no-test-deployment.yaml  # powinno zwrócić błąd/odrzucenie
5. kubectl apply -f yes-test-deployment.yaml # powinno działać
6. kubectl apply -f zero-test-deployment.yaml # powinno działać i mieć domyślne request/limit
