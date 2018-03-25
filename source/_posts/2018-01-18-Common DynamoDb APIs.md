# Common DynamoDb APIs
## Table Operations
### createTable
#### 1.Interface
	Table createTable(CreateTableRequest request);
##### Description
	Create an table in dynamoDb
##### Input
	CreateTableRequest request: amazon create table request
##### Output
	Table : amazon dynamoDb table
##### Example
	CreateTableRequest createTableRequest = new CreateTableRequest().withTableName(compositeKeyTableName)
                    .withKeySchema(new KeySchemaElement(HASH_KEY_NAME, KeyType.HASH),
                            new KeySchemaElement(RANGE_KEY_NAME, KeyType.RANGE))
                    .withAttributeDefinitions(new AttributeDefinition(HASH_KEY_NAME, ScalarAttributeType.S),
                            new AttributeDefinition(RANGE_KEY_NAME, ScalarAttributeType.S),
                            new AttributeDefinition(STR_COL_NAME, ScalarAttributeType.S),
                            new AttributeDefinition(ANOTHER_STR_COL_NAME, ScalarAttributeType.S),
                            new AttributeDefinition(INT_COL_NAME, ScalarAttributeType.N))
                    .withGlobalSecondaryIndexes(strColIndex, anotherStrColIndex, strColIntColIndex, strColAnotherStrColIndex)
                    .withProvisionedThroughput(new ProvisionedThroughput(10L, 10L));

            Table table = stringCompositeKeyEntityDao.createTable(createTableRequest);
            table.waitForActive();

### deleteTable
#### 1.Interface
	void deleteTable(String tableName);
##### Description
	Delete the table in dynamoDb
##### Input
	String tableName
##### Output
	void
###### Example
	if (dao.existTable(compositeKeyTableName)) {
            dao.deleteTable(compositeKeyTableName);
        }

### existTable
#### 1.Interface
	boolean existTable(String tableName);
##### Description
	Check whether the table exists or not
##### Input
	String tableName
##### Output
	boolean : exists or not
##### Example
	if (dao.existTable(compositeKeyTableName)) {
            dao.deleteTable(compositeKeyTableName);
        }

### createGSI
#### 1.Interface
	Index createGSI(String tableName, CreateGlobalSecondaryIndexAction createGlobalSecondaryIndexAction,
                    AttributeDefinition hashKeyDefinition);
##### Description
##### Input
##### Output
###### Example

#### 2.Interface
	Index createGSI(String tableName, CreateGlobalSecondaryIndexAction createGlobalSecondaryIndexAction,
                    AttributeDefinition hashKeyDefinition, AttributeDefinition rangeKeyDefinition);
##### Description
##### Input
##### Output
###### Example

### getTableStreamArn
#### 1.Interface
	String getTableStreamArn();
##### Description
	Get the table stream arn, it will return null when stream is not enabled
##### Input
	
##### Output
	table stream arn
##### Example

### updateTableThroughput
#### 1.Interface
	void updateTableThroughput(String tableName, Map<String, Tuple2<Long, Long>> indexMap);
##### Description
##### Input
##### Output
##### Example



## Basic Operations
### save
#### 1.Interface
	void save(@Valid @NotNull E entity);
##### Description
	
##### Input
##### Output
##### Example


#### 2.Interface
	void save(E entity, boolean retryFlag);
##### Description
	
##### Input
##### Output
##### Example

#### 3.Interface
	void save(E entity, DynamoDBMapperConfig.SaveBehavior saveBehavior);
##### Description
	
##### Input
##### Output
##### Example

### get
#### 1.Interface
	E get(@Valid @NotNull K id);
##### Description
	
##### Input
##### Output
##### Example


#### 2.Interface
	E get(@Valid @NotNull K id, boolean retryFlag);
##### Description
	
##### Input
##### Output
##### Example

#### 3.Interface
	E get(K hashKey, Projection projection);
##### Description
	
##### Input
##### Output
##### Example

#### 4.Interface
	E get(K hashKey, Object rangeKey);
##### Description
	
##### Input
##### Output
##### Example

#### 5.Interface
	E get(K hashKeyVal, Object rangeKeyVal, Projection projection);
##### Description
	
##### Input
##### Output
##### Example

### scan
#### 1.Interface
	Pagination<E> scan(CompositeScanExpression compositeScanExpression);
##### Description
	
##### Input
##### Output
##### Example

#### 2.Interface
	List<E> scanAll();
##### Description
	
##### Input
##### Output
##### Example

#### 3.Interface
	Pagination<E> scanAll(int page, int limit);
##### Description
	
##### Input
##### Output
##### Example

#### 4.Interface
	Pagination<E> scanAll(int page, int limit, Map<String, Object> params);
##### Description
	
##### Input
##### Output
##### Example

### query
#### 1.Interface
	Pagination<E> query(CompositeQueryExpression<E> compositeQueryExpression)
##### Description
	
##### Input
##### Output
##### Example

#### 2.Interface
	Pagination<E> keyQuery(String hashKeyName, Object hashKeyValue, int page, int limit);
##### Description
	
##### Input
##### Output
##### Example

#### 3.Interface
	Pagination<E> keyQuery(String hashKeyName, Object hashKeyValue, int page, int limit, Projection projection);
##### Description
	
##### Input
##### Output
##### Example

#### 4.Interface
	Pagination<E> keyQuery(String hashKeyName, Object hashKeyValue,
                                  String rangeKeyName, Object rangeKeyValue, int page, int limit);
##### Description
	
##### Input
##### Output
##### Example

#### 5.Interface
	Pagination<E> keyQuery(String hashKeyName, Object hashKeyValue,
                                  String rangeKeyName, Object rangeKeyValue,
                                  int page, int limit, Projection projection);
##### Description
	
##### Input
##### Output
##### Example

#### 6.Interface
	Pagination<E> indexQuery(String hashKeyName, Object hashKeyValue, int page, int limit);
##### Description
	
##### Input
##### Output
##### Example

#### 7.Interface
	Pagination<E> indexQuery(String hashKeyName, Object hashKeyValue, int page, int limit, Projection projection);
##### Description
	
##### Input
##### Output
##### Example

#### 8.Interface
	Pagination<E> indexQuery(String hashKeyName, Object hashKeyValue,
                                    String rangeKeyName, Object rangeKeyValue, int page, int limit);
##### Description
	
##### Input
##### Output
##### Example

#### 9.Interface
	Pagination<E> indexQuery(String hashKeyName, Object hashKeyValue,
                                    String rangeKeyName, Object rangeKeyValue,
                                    int page, int limit, Projection projection);
##### Description
	
##### Input
##### Output
##### Example

#### 10.Interface
	Pagination<E> indexQuery(String indexName, String hashKeyName, Object hashKeyValue, int page, int limit);
##### Description
	
##### Input
##### Output
##### Example

#### 11.Interface
	Pagination<E> indexQuery(String indexName, String hashKeyName, Object hashKeyValue,
                                    String rangeKeyName, Object rangeKeyValue, int page, int limit);
##### Description
	
##### Input
##### Output
##### Example

#### 12.Interface
	Pagination<E> indexQuery(String indexName, String hashKeyName, Object hashKeyValue,
                                    int page, int limit, Projection projection);
##### Description
	
##### Input
##### Output
##### Example

#### 13.Interface
	Pagination<E> indexQuery(String indexName, String hashKeyName, Object hashKeyValue,
                                    String rangeKeyName, Object rangeKeyValue, int page, int limit,
                                    Projection projection);
##### Description
	
##### Input
##### Output
##### Example

### count
#### 1.Interface
	int count(String key, String value);
##### Description
	
##### Input
##### Output
##### Example


#### 2.Interface
	int count();
##### Description
	
##### Input
##### Output
##### Example

### delete
#### 1.Interface
	void delete(K hashKey, Object rangeKey)
##### Description
##### Input
##### Output
##### Example


#### 2.Interface
	void delete(@Valid @NotNull K id);
##### Description
##### Input
##### Output
##### Example

## Batch Operations
### 
	void batchAdd(Iterable<E> toBeAdded);
	void batchAddSync(Iterable<E> toBeAdded);
	void batchAddSync(Iterable<E> toBeAdded, long timeOutInSeconds, Executor executor);
	void batchDelete(Iterable<E> toBeDeleted);
	void batchDeleteSync(Iterable<E> toBeDeleted);
	void batchDeleteSync(Iterable<E> toBeDeleted, long timeOutInSeconds, Executor executor);
	List<E> batchGet(Iterable<K> ids);
	@Deprecated
	List<E> batchGet(Iterable<K> gsiHkValIterable, final String gsiName);
	List<E> batchKeyQuerySync(String hashKeyName, Iterable<K> ids);
	List<E> batchKeyQuerySync(String hashKeyName, Iterable<K> ids, long timeOutInSeconds);
	List<E> batchKeyQuerySync(String hashKeyName, Iterable<K> ids, long timeOutInSeconds, Executor executor);
	List<E> batchGetOrderly(List<K> hashKeyValList);
	List<E> batchGetSync(Iterable<K> hkValIterable);
	List<E> batchGetSync(Iterable<K> hkValIterable, long timeOutInSeconds);
	List<E> batchGetSync(Iterable<K> hkValIterable, long timeOutInSeconds, Executor executor);
	List<E> batchGetSyncOrderly(List<K> hkValList);
	List<E> batchGetSyncOrderly(List<K> hkValList, long timeOutInSeconds);
	List<E> batchGetSyncOrderly(List<K> hkValList, long timeOutInSeconds, Executor executor);
	List<E> gsiBatchGet(final String gsiName, final String gsiHkName, Iterable<K> gsiHkValIterable);
	@Deprecated
    List<E> gsiBatchGet(final String gsiName, final String gsiHkName, Iterable<K> gsiHkValIterable, Executor executor);
    List<E> gsiBatchGetSync(final String gsiName, final String gsiHkName, Iterable<K> gsiHkValIterable);
    List<E> gsiBatchGetSync(final String gsiName, final String gsiHkName, Iterable<K> gsiHkValIterable, long
            timeOutInSeconds);
    List<E> gsiBatchGetSync(final String gsiName, final String gsiHkName, Iterable<K> gsiHkValIterable, long
            timeOutInSeconds, Executor executor);
    Map<K, E> batchGetForMap(Iterable<K> hashKeyValIterable);
    List<E> batchGetFromEntityList(Iterable<E> entityIterable);
    List<E> batchGetFromEntityListSync(Iterable<E> entityIterable);
    List<E> batchGetFromEntityListSync(Iterable<E> entityIterable, long timeOutInSeconds);
    List<E> batchGetFromEntityListSync(Iterable<E> entityIterable, long timeOutInSeconds, Executor executor);
	
#### 1.Interface
##### Description
##### Input
##### Output
##### Example