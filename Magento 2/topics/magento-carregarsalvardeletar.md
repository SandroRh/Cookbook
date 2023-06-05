## Importante

É importante frizar que o padrão do Magento 2 é utilizar uma classe Repository. Essa classe seria responsável por todas as operações relacionadas ao banco de dados, como carregar, salvar, atualizar, deletar. Nessa mesma seção existe um tutorial de como criar uma classe Repository.

## Overall

1. Necessário ter um objeto factory do Model, pois será no objeto que o factory criará que armazenaremos as informações do registro recuperado da tabela.

2. Necessário ter o ResourceModel pois é com ele que executaremos as operações de CRUD.

## Código de exemplo

```php

use FCamara\B2E\Model\CouponFactory;
use FCamara\B2E\Model\ResourceModel\Coupon\CollectionFactory;
use FCamara\B2E\Model\ResourceModel\Coupon as CouponResourceModel;

class CouponRepository 
{
    /** @var CouponFactory */
    private CouponFactory $couponFactory;
    /** @var CollectionFactory */
    private CollectionFactory $couponCollectionFactory;
    /** @var CouponResourceModel */
    private CouponResourceModel $couponResourceModel;

    /**
     * @param CouponFactory $couponFactory
     * @param CouponResourceModel $couponResourceModel
     * @param CollectionFactory $couponCollectionFactory
     */
    public function __construct(
        CouponFactory $couponFactory,
        CouponResourceModel $couponResourceModel,
        CollectionFactory $couponCollectionFactory
    ) {
        $this->couponFactory = $couponFactory;
        $this->couponResourceModel = $couponResourceModel;
        $this->couponCollectionFactory = $couponCollectionFactory;
    }

    /**
     * Como carregar um cupom (exemplo) 
     */
    public function load($id) 
    {
        $coupon = $this->couponFactory->create();
        $this->couponResourceModel->load($coupon, $id);
        return $coupon;
    }

    /**
     * Como carregar um cupom por um field específico
     * No nosso caso, taxvat
     */
    public function loadByTaxvat() 
    {
        $coupon = $this->couponFactory->create();
        $taxvat = "12345678910";
        $this->couponResourceModel->load($coupon, $taxvat, 'taxvat');
        return $coupon;
    }

    /**
     * Como deletar um cupom (exemplo) 
     */
    public function delete($id) 
    {
        $coupon = $this->couponFactory->create();
        $this->couponResourceModel->load($coupon, $id);
        $this->couponResourceModel->delete($coupon);
    }

    /**
     * Como salvar um cupom (exemplo) 
     */
    public function save() 
    {
        $coupon = $this->couponFactory->create();
        $this->couponResourceModel->load($coupon, $id);
        $coupon->setGroupCode("Exemplo");
        $this->couponResourceModel->save($coupon);
    }
}

```