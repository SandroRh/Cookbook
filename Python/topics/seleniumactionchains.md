# Action Chains
Um guia sobre os comandos disponíveis para o mouse, como segurar e arrastar.

## Start Guide

    from selenium.webdriver import ActionChains

    actions = ActionChains(driver)
    actions.click_and_hold(bater_ponto).perform()