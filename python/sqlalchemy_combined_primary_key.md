# SQL Alchemy combined primary key 


SQL
```
CREATE TABLE person_location (
    person_uuid UUID NOT NULL, 
    location_uuid UUID NOT NULL, 
    CONSTRAINT person_location_pk PRIMARY KEY (person_uuid, location_uuid)
)
```

Model
```
class PersonLocation(Base):
    __tablename__ = 'person_location'
    person_uuid = Column(UUIDType, primary_key=True)
    location_uuid = Column(UUIDType, primary_key=True)
```

or 

```
class PersonLocation(Base):
    __tablename__ = 'person_location'
    __table_args__ = (
        PrimaryKeyConstraint('person_uuid', 'location_uuid'),
        {},
    )
    person_uuid = Column(UUIDType)
    location_uuid = Column(UUIDType)
```