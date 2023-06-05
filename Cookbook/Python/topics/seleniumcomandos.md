# Comandos
Um guia sobre os comandos disponíveis do selenium.

## Ir para uma URL

    driver.get("https://infracommerce132357.protheus.cloudtotvs.com.br:4020/meurh01/#/login")

## Encontrar um elemento

    usuario = driver.find_element(By.XPATH, "/html/body/app-root/div/div/app-login/div[1]/div/form/po-input/po-field-container/div/div[2]/input")

## Enviar texto

    usuario.send_keys("19116122712")