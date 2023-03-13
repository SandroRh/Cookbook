# Passos

- Criar interface

`Vendor/Module/Api/Data/ModelInterface`
`Infracommerce/SubscriptionsAnalysis/Api/Data/SubscriptionsAnalysisInterface`

```php
<?php

namespace Infracommerce\SubscriptionsAnalysis\Api\Data;

interface SubscriptionsAnalysisInterface
{
    public const SUBSCRIPTION_ID = 'subscription_id';
    public const CREATED_AT = 'created_at';
    public const STATUS = 'status';
    public const COMMENTS = 'comments';
    public const STATUS_WAITING = 'waiting';
    public const STATUS_APPROVED = 'approved';
    public const STATUS_DENIED = 'denied';

    /**
     * Get Subscription Id.
     *
     * @return string
     */
    public function getSubscriptionId(): string;

    /**
     * Set Subscription Id.
     *
     * @param string $subscriptionId
     * @return void
     */
    public function setSubscriptionId(string $subscriptionId): void;

    /**
     * Get Created At.
     *
     * @return string
     */
    public function getCreatedAt(): string;

    /**
     * Set Created At.
     *
     * @param string $createdAt
     * @return void
     */
    public function setCreatedAt(string $createdAt): void;

    /**
     * Get Status.
     *
     * @return string
     */
    public function getStatus(): string;

    /**
     * Set Status.
     *
     * @param string $status
     * @return void
     */
    public function setStatus(string $status): void;

    /**
     * Get Comments.
     *
     * @return string
     */
    public function getComments(): string;

    /**
     * Set Comments.
     *
     * @param string $comments
     * @return void
     */
    public function setComments(string $comments): void;
}
```